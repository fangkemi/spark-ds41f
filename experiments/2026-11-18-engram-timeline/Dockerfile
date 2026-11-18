FROM spark-ds41f:c61-c0e4124-timeline-20261118
LABEL local.spark-ds41f.vllm.tree="1543ef317f6e0387f15fdaf061034a062df8f2da" local.spark-ds41f.vllm.patch-head="4732b166ec3e4de65ea395f11ea8a89ab985ef41" local.spark-ds41f.build-mode="engram-timeline-complete" local.spark-ds41f.parent-image-id="sha256:e88f679d9a7d5d67c8a9f052c48e638c76856cf8432ff1872e590c2b707fa95b"
COPY . /opt/spark-ds41f/candidate/vllm/
RUN find /opt/spark-ds41f/candidate/vllm -type d -name __pycache__ -prune -exec rm -rf '{}' +
RUN python3 -c 'from vllm.models.deepseek_v4_1.engram_rows._native import prebuild; print(prebuild())'
