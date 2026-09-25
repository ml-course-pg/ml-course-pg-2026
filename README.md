# Uczenie maszynowe w Pythonie — kurs 2026

Materiały do zajęć z uczenia maszynowego. Z każdych zajęć znajdziesz tutaj notebook z ćwiczeniami oraz — jeśli jest — zadanie do wykonania.

Notebooki możesz uruchomić na dwa sposoby:

- **[A. Lokalnie na swoim komputerze](#a-lokalnie-na-swoim-komputerze-od-zera)** — raz instalujesz wszystko, potem pracujesz offline.
- **[B. W Google Colab](#b-google-colab-bez-instalacji)** — w przeglądarce, bez instalowania czegokolwiek. Wystarczy konto Google.

Nie wiesz, co wybrać? Zacznij od **Colaba** — działa od razu.

---

## A. Lokalnie na swoim komputerze (od zera)

Instrukcja zakłada nowy laptop, na którym nic nie ma. Każde polecenie wpisujesz w **terminalu**:

- **Windows:** menu Start → wpisz `cmd` → „Wiersz polecenia” (albo „PowerShell”)
- **macOS:** Cmd + Spacja → wpisz `Terminal`
- **Linux:** Ctrl + Alt + T

### Krok 1. Zainstaluj Git

Git służy do pobierania repozytorium (i jego aktualizacji w trakcie kursu).

1. Pobierz instalator: **<https://git-scm.com/downloads>** i zainstaluj z domyślnymi ustawieniami.
2. Sprawdź, czy działa (zamknij i otwórz terminal ponownie):
   ```bash
   git --version
   ```
   Powinno się pojawić np. `git version 2.46.0`.

Więcej: [Set up Git — dokumentacja GitHuba](https://docs.github.com/en/get-started/git-basics/set-up-git).

### Krok 2. Zainstaluj Pythona

Potrzebny jest **Python 3.10 lub nowszy** (polecamy najnowszą stabilną wersję).

1. Pobierz instalator: **<https://www.python.org/downloads/>**
2. Zainstaluj:
   - **Windows:** w pierwszym oknie instalatora **zaznacz „Add python.exe to PATH”** — bez tego terminal nie znajdzie Pythona. ([instrukcja dla Windows](https://docs.python.org/3/using/windows.html))
   - **macOS:** uruchom pobrany plik `.pkg` i przejdź przez instalator. ([instrukcja dla macOS](https://docs.python.org/3/using/mac.html))
3. Sprawdź wersję (zamknij i otwórz terminal ponownie):
   ```bash
   python --version      # Windows
   python3 --version     # macOS / Linux
   ```
   Powinno się pojawić np. `Python 3.13.7`.

> Dalej w instrukcji piszemy `python`. Na **macOS/Linux** wpisuj zamiast tego `python3`.

### Krok 3. Pobierz repozytorium

Przejdź do folderu, w którym chcesz trzymać materiały (np. Dokumenty), i sklonuj repozytorium:

```bash
cd Documents
git clone https://github.com/ml-course-pg/ml-course-pg-2026.git
cd ml-course-pg-2026
```

Powstanie folder `ml-course-pg-2026` ze wszystkimi materiałami.

### Krok 4. Utwórz środowisko wirtualne

Środowisko wirtualne (`.venv`) to osobna „szuflada” na biblioteki tego kursu — nie miesza się z innymi projektami. ([więcej o venv](https://docs.python.org/3/library/venv.html))

Będąc w folderze `ml-course-pg-2026`:

```bash
python -m venv .venv
```

Następnie **aktywuj** środowisko:

| system | polecenie |
|---|---|
| Windows (Wiersz polecenia / cmd) | `.venv\Scripts\activate` |
| Windows (PowerShell) | `.venv\Scripts\Activate.ps1` |
| macOS / Linux | `source .venv/bin/activate` |

Po aktywacji na początku linii terminala pojawi się `(.venv)` — to znak, że wszystko jest dobrze.


### Krok 5. Zainstaluj biblioteki

W aktywnym środowisku (`(.venv)` na początku linii):

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Instalacja potrwa kilka minut — pobiera m.in. numpy, pandas, scikit-learn i Jupytera.

### Krok 6. Uruchom Jupyter Notebook

```bash
jupyter notebook
```

Otworzy się przeglądarka z listą plików. Wejdź do folderu z zajęciami (np. `01-wprowadzenie`) i kliknij notebook (plik `.ipynb`).

- komórkę uruchamiasz: **Shift + Enter**
- wszystkie komórki naraz: menu **Run → Run All Cells**
- zakończenie pracy: zamknij kartę przeglądarki, a w terminalu naciśnij **Ctrl + C**

Więcej: [instalacja i uruchamianie Jupytera](https://jupyter.org/install).


### Przy kolejnych zajęciach

Nie instalujesz niczego od nowa. Wystarczy:

```bash
cd Documents/ml-course-pg-2026
git pull                          # pobierz nowe materiały
.venv\Scripts\activate            # Windows (macOS/Linux: source .venv/bin/activate)
jupyter notebook
```

> **Wskazówka:** zanim zaczniesz edytować notebook, zapisz jego kopię pod inną nazwą (**File → Save As…**, np. `01_demo_moje.ipynb`). Wtedy `git pull` nie będzie się kłócił z Twoimi zmianami.

### Najczęstsze problemy

| problem | rozwiązanie |
|---|---|
| `python` / `git` „nie jest rozpoznawany” | zamknij i otwórz terminal po instalacji; na Windows zainstaluj Pythona ponownie z zaznaczonym „Add python.exe to PATH” |
| `ModuleNotFoundError: No module named 'sklearn'` | środowisko nie jest aktywne — aktywuj je (krok 4) i uruchom `jupyter notebook` jeszcze raz |
| `ImportError: cannot import name 'root_mean_squared_error'` | masz za stary scikit-learn — w aktywnym środowisku: `pip install --upgrade -r requirements.txt` |
| `FileNotFoundError` przy wczytywaniu danych | uruchom Jupytera z folderu `ml-course-pg-2026`, a notebook otwórz z jego folderu (np. `01-wprowadzenie`) |

---

## B. Google Colab (bez instalacji)

Colab uruchamia notebooki w przeglądarce, na serwerach Google. Wszystkie potrzebne biblioteki są już zainstalowane, a dane pobierają się automatycznie z tego repozytorium.

1. Zaloguj się na konto Google.
2. Otwórz notebook jednym kliknięciem:

   | zajęcia | notebook |
   |---|---|
   | 1 — demo | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ml-course-pg/ml-course-pg-2026/blob/main/01-wprowadzenie/01_demo_workflow_ml.ipynb) `01_demo_workflow_ml.ipynb` |
   | 1 — zadanie grupowe | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ml-course-pg/ml-course-pg-2026/blob/main/01-wprowadzenie/02_zadanie_grupowe_hotele.ipynb) `02_zadanie_grupowe_hotele.ipynb` |

   Każdy inny notebook otworzysz przez **<https://colab.research.google.com>** → **File → Open notebook → GitHub** → wklej `ml-course-pg/ml-course-pg-2026`.
3. **Zapisz własną kopię:** **File → Save a copy in Drive**. Bez tego Twoje zmiany przepadną po zamknięciu karty.
4. Uruchamiaj komórki **Shift + Enter** albo wszystkie naraz: **Runtime → Run all**.

**Pliki zapisywane w notebooku** (np. `grupa_XX.joblib` z zadania grupowego) trafiają na tymczasowy dysk Colaba i znikają po zamknięciu sesji. Pobierzesz je przez ikonę folderu po lewej stronie → prawy klik na pliku → **Download**.
