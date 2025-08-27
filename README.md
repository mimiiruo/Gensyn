# Move Gensyn Nodes to New VPS

*By FasoNodes — Aug 27, 2025*

---

## Step 1: Make 100GB Swap

```bash
rm -rf create-swap-100.sh && \
wget https://raw.githubusercontent.com/ezlabsnodes/autoinstall/main/create-swap-100.sh && \
chmod +x create-swap-100.sh && \
sudo ./create-swap-100.sh
```

---

## Step 2: Install Dependency

```bash
rm -rf depedency-nodejs.sh && \
wget https://raw.githubusercontent.com/ezlabsnodes/autoinstall/main/depedency-nodejs.sh && \
chmod +x depedency-nodejs.sh && \
sudo ./depedency-nodejs.sh
```

---

## Step 3: Create Directory ezlabs

```bash
mkdir /root/ezlabs
```

Copy the following three files into `/root/ezlabs/`:

- `swarm.pem`
- `userApiKey.json`
- `userData.json`

---

## Step 4: Run Gensyn Node

```bash
cd && rm -rf updateofficial.sh officialauto.zip && \
wget https://raw.githubusercontent.com/ezlabsnodes/gensyn/main/updateofficial.sh && \
chmod +x updateofficial.sh && \
./updateofficial.sh
```

✅ **All Done**

---

## (Optional) Use Systemd Instead of Screen

One-click command to migrate:

```bash
wget -O systemd.sh https://raw.githubusercontent.com/ezlabsnodes/gensyn/main/systemd.sh && \
chmod +x systemd.sh && \
./systemd.sh
```
