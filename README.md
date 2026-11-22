# ForgeMinerTools

Files that [ForgeMiner](https://github.com/0xHashRaptor/ForgeMiner) fetches for its tools, kept where they can be reached from anywhere.

## NVIDIA driver 610.43.03 (for the CMP unlock)

The CMP hardware unlock (`sudo forge --cmp-install`) is built against the NVIDIA Linux driver **610.43.03**. HiveOS's own driver list
stops before the 610 series, and NVIDIA's download server is not reachable from every network, so the installer is mirrored here.

Release [`nvidia-610.43.03`](https://github.com/0xHashRaptor/ForgeMinerTools/releases/tag/nvidia-610.43.03):

| File | Size | SHA-256 |
|---|---|---|
| `NVIDIA-Linux-x86_64-610.43.03.run` | 461 538 429 bytes | `45e2d4c134a23c35e50f253a4aa63e7e5e8d17e3d185d4a07c8a58e9612ed392` |
| `NVIDIA-LICENSE` | 22 653 bytes | `c692fb14ad4f499c6aee1b9e144e6905148c420e6225b17cb2937366c1e507ad` |

- The installer is NVIDIA's file exactly as NVIDIA publishes it, byte for byte: the same SHA-256 as
  `https://download.nvidia.com/XFree86/Linux-x86_64/610.43.03/NVIDIA-Linux-x86_64-610.43.03.run`.
- It is redistributed under section 1.1(d) of the NVIDIA Driver License Agreement, whose full text (`NVIDIA-LICENSE`, taken from the
  installer itself) comes with it.
- The NVIDIA driver is NVIDIA's software and stays under NVIDIA's license; it is not part of ForgeMiner.

### Use

ForgeMiner 2.1.2 and newer download it, check the SHA-256 and install it in one step (HiveOS: through `nvidia-driver-update`):

```bash
sudo forge --cmp-driver      # the driver (this mirror first, then NVIDIA's server)
sudo reboot
sudo forge --cmp-install     # the CMP unlock
```

By hand on HiveOS:

```bash
cd /hive-drivers-pack
wget https://github.com/0xHashRaptor/ForgeMinerTools/releases/download/nvidia-610.43.03/NVIDIA-Linux-x86_64-610.43.03.run
sha256sum NVIDIA-Linux-x86_64-610.43.03.run    # must print 45e2d4c1...e9612ed392
nvidia-driver-update /hive-drivers-pack/NVIDIA-Linux-x86_64-610.43.03.run
```

---

## Драйвер NVIDIA 610.43.03 (для разлока CMP)

Разлок CMP (`sudo forge --cmp-install`) собирается под драйвер NVIDIA **610.43.03**. В списке драйверов HiveOS серии 610 нет, а сервер
NVIDIA доступен не из всех сетей, поэтому установщик лежит здесь — тот же файл, что у NVIDIA, байт в байт (сумма SHA-256 выше), с полным
текстом лицензии NVIDIA рядом (пункт 1.1(d) лицензии разрешает такое распространение).

ForgeMiner 2.1.2 и новее скачивают его, проверяют сумму и ставят одной командой: `sudo forge --cmp-driver`, затем перезагрузка и
`sudo forge --cmp-install`.
