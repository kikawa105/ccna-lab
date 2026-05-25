# LACP EtherChannel Lab

## 概要
Cisco Packet Tracer を使用して
LACP EtherChannel を構築。

## 目的
- EtherChannel の理解
- LACP の動作確認
- trunk link の構築
- Native VLAN の設定

---

# トポロジ

SW1 <----> SW2

<img width="1470" height="956" alt="スクリーンショット 2026-05-25 16 44 58" src="https://github.com/user-attachments/assets/20b9be6a-e7ba-4a89-969d-60879b9a8774" />


使用ポート
- Fa0/1
- Fa0/2

---

# 使用技術

- EtherChannel
- LACP
- trunk
- 802.1Q
- Native VLAN

---

# SW1 Config

```cisco
interface range fa0/1 - 2
 channel-group 1 mode active

interface port-channel 1
 switchport mode trunk
 switchport trunk native vlan 10
```

---

# SW2 Config

```cisco
interface range fa0/1 - 2
 channel-group 1 mode active

interface port-channel 1
 switchport mode trunk
 switchport trunk native vlan 10
```

---

# 確認コマンド

## EtherChannel確認

```cisco
show etherchannel summary
```
<img width="470" height="209" alt="スクリーンショット 2026-05-25 16 45 33" src="https://github.com/user-attachments/assets/b87457af-6e50-40bd-80e8-653e8395484d" />

```text
Po1(SU) LACP Fa0/1(P) Fa0/2(P)
```

---

## trunk確認

```cisco
show interfaces trunk
```

結果

```text
Po1  on  802.1q  trunking  10
```
<img width="404" height="142" alt="スクリーンショット 2026-05-25 16 47 52" src="https://github.com/user-attachments/assets/437b4412-2990-44f7-9bb4-1b3b4016f6c6" />

---

# 学んだこと

- EtherChannel は複数リンクを1本として扱える
- LACP は動的ネゴシエーション
- trunk設定は両側一致が重要

---

# 使用ツール

- Cisco Packet Tracer
