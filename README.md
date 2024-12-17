```
async updateOrCreate2({ data = [] }: RegionListDto) {
  data.forEach((item) => {
    if (item.id) checkInvalidFields(RegionUpdateDto, item);
    else checkInvalidFields(RegionCreateDto, item);
  });

  return await Promise.all(
    data.map(({ id, ...others }) => {
      if (id)
        return this.prismaService.regions.update({
          where: { id },
          data: others,
        });
      else return this.prismaService.regions.create({ data: others });
    }),
  );
}
```
