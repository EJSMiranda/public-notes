# Add or Remove "Console lock display off timeout" in Power Options using Command Prompt

1. Open an elevated command prompt.
2. Type the command below you want to use into the elevated command prompt, and press Enter.

## Add the setting key to the registry

```powershell
REG ADD HKLM\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\7516b95f-f776-4464-8c53-06167f40cc99\8EC4B3A5-6868-48c2-BE75-4F3044BE88A7 /v Attributes /t REG_DWORD /d 2 /f
```

## Update the Power Options

### For AC power

```powershell
powercfg /SETACVALUEINDEX SCHEME_CURRENT SUB_VIDEO VIDEOCONLOCK <seconds>​
```

### For DC power

```powershell
powercfg /SETDCVALUEINDEX SCHEME_CURRENT SUB_VIDEO VIDEOCONLOCK <seconds>
```

## Disable the setting (Return to default)

```powershell
powercfg -attributes SUB_VIDEO 8EC4B3A5-6868-48c2-BE75-4F3044BE88A7 +ATTRIB_HIDE
```
