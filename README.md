import { Injectable, OnApplicationShutdown } from '@nestjs/common';
import { Consumer, Kafka, logLevel, CompressionTypes, CompressionCodecs } from 'kafkajs';
import ZstdCodec from '@kafkajs/zstd';
import { PrismaService } from '../prisma/prisma.service';
import { writeFile } from 'node:fs';

CompressionCodecs[CompressionTypes.ZSTD] = ZstdCodec()
