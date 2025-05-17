FROM mwader/static-ffmpeg AS ffmpeg

FROM osamir27/upx:latest AS upx

WORKDIR /tmp

COPY --from=ffmpeg /ffmpeg ./ffmpeg-big
COPY --from=ffmpeg /ffprobe ./ffprobe-big

RUN upx -9 --lzma -o ./ffmpeg ./ffmpeg-big
RUN upx -9 --lzma -o ./ffprobe ./ffprobe-big
RUN chmod +x ./ffmpeg ./ffprobe

FROM scratch
COPY --from=upx /tmp/ffmpeg /ffmpeg
COPY --from=upx /tmp/ffprobe /ffprobe

