# VoIP VLAN Lab

## 構成
- Router 1941
- Switch 2960
- Cisco IP Phone 7960
- PC

## 目的
Cisco IP Phone を使用した Voice VLAN の理解

## 学習内容
- access vlan
- voice vlan
- PC → Phone → Switch の接続
- Cisco IP Phone の動作理解

- ## 初期配線
- <img width="1470" height="956" alt="スクリーンショット 2026-05-25 11 35 45" src="https://github.com/user-attachments/assets/d8e1657b-696d-46b2-b29b-93464b328583" />


## Switch 2960の設定
-　エラー発生「extended VLAN(s) not allowed in current VTP mode」
- 2960スイッチが VTP Server modeになってるため発生したエラー。
- このモードだと、Extended VLAN（1006〜4094）の作成が不可。
- 「vtp mode transparent」で解決。
<img width="716" height="347" alt="スクリーンショット 2026-05-25 11 44 42" src="https://github.com/user-attachments/assets/eee49743-b3ad-41c9-8a44-ca517efeb3ab" />
- VLANには2種類ある　Normal Range VLAN（1〜1005）普通のVLAN　Extended Range VLAN（1006〜4094）拡張VLAN

- Voice VLANとデータVLANを分ける
- <img width="622" height="247" alt="スクリーンショット 2026-05-25 11 56 23" src="https://github.com/user-attachments/assets/a73bf7b0-dc09-4be5-888c-d3c605fccf31" />



- show vlan briefで確認
<img width="496" height="223" alt="スクリーンショット 2026-05-25 12 01 53" src="https://github.com/user-attachments/assets/294f50e2-c624-4684-bb21-b9fabd20dd71" />
- 有効化されている

## 検証結果

show running-config にて
以下設定を確認。

```cisco
interface FastEthernet0/1
 switchport access vlan 400
 switchport mode access
 switchport voice vlan 2001
 spanning-tree portfast
```
