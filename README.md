# GUI Silnik V1.0 – Darmowy silnik aplikacji w Pythonie (PyQt5)  
**Open-source engine for building modular GUI apps using PyQt5.**

---

## 🧠 Opis (PL)

**GUI Silnik V1.0** to modularny, w pełni konfigurowalny silnik do tworzenia własnych aplikacji w Pythonie z użyciem PyQt5.  
Zapewnia gotowy system:

- dynamicznego ładowania widżetów (widgets)
- motywów i stylów (themes)
- tłumaczeń, promptów i zarządzania tagami
- edycji ustawień z poziomu GUI
- integracji z ComfyUI, AI itp.

### 🔓 Licencja

Ten silnik udostępniany jest **za darmo na licencji MIT**.  
**Wszystkie widżety z folderu `widzety/` mogą mieć osobne licencje** (darmowe lub płatne).

---

## 🧠 Description (EN)

**GUI Engine V1.0** is a modular and fully customizable GUI engine for building Python apps using PyQt5.  
It features:

- dynamic widget system
- theming/styling support
- translations, prompt management
- GUI-based settings editor
- support for ComfyUI, AI tools etc.

### 🔓 License

The core engine is released under the **MIT License**.  
**Individual widgets in `widzety/` may use their own licenses** (free or paid).

---

## 📦 Foldery / Folders

```
📁 gui/                → główna logika GUI
📁 widzety/            → Twoje własne widżety (apps)
📁 config/             → ustawienia i motywy
📁 style/              → pliki graficzne
📁 logs/               → logi działania
📁 bin/                → pliki startowe
main.py               → uruchamianie aplikacji
```

---

## 🛠️ Wymagania / Requirements

- Python 3.10+
- PyQt5
- json, os, shutil (wbudowane)

---

## 🚀 Uruchomienie / Running

Windows (PowerShell lub `.bat`):

```bash
cd "ścieżka/do/folderu"
python run.py
```

Lub:

```bash
bin/start.bat
```

---

## ✨ Przykład aplikacji / Demo apps

Silnik zawiera testowe widżety:  
- generator promptów AI  
- widok i tłumaczenie tagów  
- edytor promptów ComfyUI  
- konsola logów



# 🧩 Tworzenie własnych widżetów (widgetów)

Ten projekt wspiera dynamiczne ładowanie widżetów z osobnych folderów. Każdy widżet to **osobny pakiet** zawierający własne pliki.

## ✅ Minimalna struktura widżetu

```
widzety/
└── przykladowywidget/
    ├── __init__.py
    └── widget.py
```

---

## 📁 __init__.py

Ten plik jest wymagany. Powinien zawierać jedną linię:

```python
from .widget import WidgetPrzykladowy as Widget
```

Dzięki temu silnik będzie wiedział, którą klasę ładować jako `Widget`.

---

## 📄 widget.py

```python
# -*- coding: utf-8 -*-
from PyQt5.QtWidgets import QWidget, QLabel, QVBoxLayout

class WidgetPrzykladowy(QWidget):
    def __init__(self, settings=None):
        super().__init__()
        self.setObjectName("widget")
        layout = QVBoxLayout(self)

        label = QLabel("To jest przykładowy widżet")
        layout.addWidget(label)

        try:
            from core.style_applier import apply_component_styles
            apply_component_styles(self, "widget")
            apply_component_styles(label, "label")
        except Exception as e:
            print(f"[STYLE WARNING] {e}")
```

---

## ⚙️ Przykład wpisu w `widgets.json`

```json
{
  "module": "przykladowywidget",
  "class": "WidgetPrzykladowy",
  "position": "center"
}
```

---

## 🔄 Widżet zostanie automatycznie wczytany przy uruchomieniu aplikacji, a jego styl zostanie zastosowany zgodnie z ustawieniami `style_overrides`.

---

## 🤝 Autor

Silnik stworzony przez: **vulpix0991**  
Pomysł, kod i struktura – 100% open source (core silnika)
