# monit-esxcli-ssacli
It is a monitoring tool when changing status of HPE Smart Array RAID informations,
for VMware ESXi (6.0 and/or above) via SSH (Remote TSM - technical support mode).

It should be installed to /usr/local/libexec (or /usr/libexec) directory, and you
can call it with `SERVERNAME(or IP address)`.

Also, you can setup a monit configuration like following:

## monit-esxcli-ssacli.monitrc
```text
CHECK PROGRAM "RAID_esxi.example.jp" WITH PATH "/usr/local/libexec/monit-esxcli-ssacli esxi.example.jp"
  EVERY "0 * * * *"
    ALERT emergency@example.jp ONLY ON { STATUS }
  IF STATUS != 0 THEN ALERT
```

## Tested and Supported VMware ESXi.
- VMware ESXi 6.0, 6.0U1, 6.0U2, 6.0U3, 6.5, 6.5U1 with [Custom HPE ESXi Image](https://www.hpe.com/info/esxidownload)
- If you use ESXi 5.5 and/or bellow, you should modify the script, like following:
  - 'sed -e "s/ssacli/hpssacli/g" monit-esxcli-ssacli > monit-esxcli-hpssacli`

## Tested environments
I confirmed follwoing environments.
- HP Smart Array P400i   (hpssacli)
- HP Smart Array P410i   (hpssacli)
- HP Smart Array P212    (hpssacli)
- HP Smart Array P420i   (hpssacli)
- HP Smart Array B120i   (hpssacli, ssacli)
- HP Smart Array P420i   (ssacli)
- HPE Smart Array B140i  (ssacli)
- HPE Smart Array P440ar (ssacli)
- HPE Smart Array P840   (ssacli)

## SEE ALSO
- [Using HPE Custom ESXi Images to Install ESXi on HPE ProLiant Servers](https://www.hpe.com/info/esxidownload)
- [HPE Smart Storage Administrator - HPE Support Center](https://www.hpe.com/support/ssa)
- [HPE Smart Storage Administrator User Guide](https://www.hpe.com/support/SSA_UG_en) ([Japanese](https://www.hpe.com/support/SSA_UG_ja))
- [Configuring Arrays on HP Smart Array Controllers Reference Guide](https://www.hpe.com/support/CASAC_RG_en) ([Japanese](https://www.hpe.com/support/CASAC_RG_jp))
- [HPE ProLiant Gen9 Troubleshooting Guide Volume I:  Troubleshooting](https://www.hpe.com/support/Gen9_TSG_en) ([Japanese](https://www.hpe.com/support/Gen9_TSG_ja))
- [HPE ProLiant Gen9 Troubleshooting Guide Volume II: Error Message](https://www.hpe.com/support/Gen9_EMG_en) ([Japanese](https://www.hpe.com/support/Gen9_EMG_ja))
- [HPE ProLiant Gen8 Troubleshooting Guide Volume I:  Troubleshooting](https://www.hpe.com/support/ProLiant_TSG_v1_en) ([Japanese](https://www.hpe.com/support/ProLiant_TSG_v1_jp))
- [HPE ProLiant Gen8 Troubleshooting Guide Volume II: Error Message](https://www.hpe.com/support/ProLiant_EMG_v1_en) ([Japanese](https://www.hpe.com/support/ProLiant_EMG_v1_jp))

## Sponsored
[Entermotion Inc.](http://entermotion.jp/) (Japanese only)
