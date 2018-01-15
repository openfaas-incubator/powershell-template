FROM microsoft/powershell:ubuntu16.04

RUN curl -sSL https://github.com/openfaas/faas/releases/download/0.6.15/fwatchdog > /usr/bin/fwatchdog \
    && chmod +x /usr/bin/fwatchdog
WORKDIR /root/

COPY function function

ENV fprocess="pwsh ./function/handler.ps1"

HEALTHCHECK --interval=1s CMD [ -e /tmp/.lock ] || exit 1

CMD ["fwatchdog"]

