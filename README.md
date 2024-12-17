async updateOrCreate({ data = [] }: RegionListDto) {
  data.forEach((item) => {
    if (item.id) checkInvalidFields(RegionUpdateDto, item);
    else checkInvalidFields(RegionCreateDto, item);
  });

  return await Promise.all(
    data.map(({ id, ...others }) => {
      if (id)
        return this.prismaService.regions.upsert({
          where: { id },
          update: others,
          create: others,
        });
      else return this.prismaService.regions.create({ data: others });
    }),
  );
}
