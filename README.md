[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112736&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** levuanhhahaha@gmail.com  
**Name:** levuanh2
---

## Mo ta

Bai lab nay khao sat tac dong cua Data Quality len hieu suat AI Agent.xay dung mot ETL Pipeline de lam sach du lieu, sau do so sanh ket qua khi Agent xu ly:
- **Clean Data** (`processed_data.csv`): Da duoc validate va lam sach
- **Garbage Data** (`garbage_data.csv`): Chua nhieu van de: duplicate ID, wrong type, outlier, null values

Ket qua cho thay: "Garbage in, garbage out" — AI Agent chi hoat dong tot khi du lieu dau vao chat luong cao.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Chay Agent voi Clean Data
python agent_simulation.py processed_data.csv

# Chay Agent voi Garbage Data
python agent_simulation.py garbage_data.csv

# So sanh ket qua: Clean Data cho ket qua tot hon, Garbage Data cho ket qua sai
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Input**: 7 records trong `garbage_data.csv`
- **Clean Data output**: 4 valid records (Laptop, Banana, Apple, Nuclear Reactor gia $1200)
- **Records bi loai bo**: 3 records (ID trung, gia string, gia NULL)
- **Agent accuracy**: Clean Data = 9/10, Garbage Data = 3/10
- **Ke luan**: Data Quality quyet dinh AI Agent output
