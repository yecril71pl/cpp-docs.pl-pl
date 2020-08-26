---
title: Dodawanie zmiennej składowej
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.variable
- vc.codewiz.variable.overview
helpviewer_keywords:
- member variables, adding
- member variables
- add member variable wizard [C++]
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
ms.openlocfilehash: e7fd5bd93198c494f18fe18755d13d40fe7fbf96
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845136"
---
# <a name="add-a-member-variable"></a>Dodawanie zmiennej składowej

Można dodać zmienną członkowską do klasy przy użyciu Widok klasy. Zmienne składowe mogą mieć na celu [wymianę danych i sprawdzanie poprawności danych](../mfc/dialog-data-exchange-and-validation.md)albo mogą być ogólne. Kreator zmiennej składowej danych został zaprojektowany w celu uzyskania odpowiednich informacji i używania go do wstawiania elementów w plikach źródłowych w odpowiednich lokalizacjach. Można dodać zmienną członkowską z [edytora okien dialogowych](../windows/dialog-editor.md) w [Widok zasobów](../windows/how-to-create-a-resource-script-file.md#create-resources)lub z [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
> Podczas projektowania i implementowania okna dialogowego może być bardziej wydajne użycie edytora okien dialogowych, aby dodać kontrolki okna dialogowego, a następnie zaimplementować zmienne składowe formantów.

**Aby dodać zmienną członkowską dla formantu okna dialogowego w Widok zasobów przy użyciu Kreatora dodawania zmiennej składowej:**

1. W Widok zasobów rozwiń węzeł projektu i węzeł okna dialogowego, aby wyświetlić listę okien dialogowych projektu.

1. Kliknij dwukrotnie okno dialogowe, do którego chcesz dodać zmienną elementu członkowskiego, aby otworzyć ją w edytorze okien dialogowych.

1. W oknie dialogowym wyświetlanym w edytorze okien dialogowych kliknij prawym przyciskiem myszy kontrolkę, do której chcesz dodać zmienną członkowską.

1. W menu skrótów wybierz polecenie **Dodaj zmienną** , aby wyświetlić [Kreatora dodawania zmiennej członkowskiej](#add-member-variable-wizard).

   > [!NOTE]
   > Wartość domyślna jest już podana w **identyfikatorze kontrolki**.

1. Podaj informacje w odpowiednich oknach kreatora. Aby uzyskać więcej informacji, zobacz [kontrolki okna dialogowego i typy zmiennych](#dialog-box-controls-and-variable-types).

1. Wybierz pozycję **Zakończ** , aby dodać definicję i kod implementacji do projektu, a następnie zamknij kreatora.

**Aby dodać zmienną członkowską z Widok klasy przy użyciu Kreatora dodawania zmiennej członkowskiej:**

1. W [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code)rozwiń węzeł projektu, aby wyświetlić klasy w projekcie.

1. Kliknij prawym przyciskiem myszy klasę, do której chcesz dodać zmienną.

1. W menu skrótów wybierz polecenie **Dodaj**, a następnie wybierz polecenie **Dodaj zmienną** , aby wyświetlić Kreatora dodawania zmiennej członkowskiej.

1. Podaj informacje w odpowiednich oknach kreatora. Aby uzyskać więcej informacji, zobacz [Kreator dodawania zmiennej członkowskiej](#add-member-variable-wizard).

1. Wybierz pozycję **Zakończ** , aby dodać definicję i kod implementacji do projektu, a następnie zamknij kreatora.

## <a name="in-this-section"></a>W tej sekcji

- [Kreator dodawania zmiennej członkowskiej](#add-member-variable-wizard)
- [Kontrolki okna dialogowego i typy zmiennych](#dialog-box-controls-and-variable-types)

## <a name="add-member-variable-wizard"></a>Kreator dodawania zmiennej członkowskiej

Ten Kreator dodaje deklarację zmiennej składowej do pliku nagłówkowego. W zależności od opcji można dodać kod do pliku. cpp. Po dodaniu zmiennej składowej za pomocą kreatora można edytować kod w środowisku deweloperskim.

- **Dostęp**

  Ustawia dostęp do zmiennej składowej. Modyfikatory dostępu są słowami kluczowymi, które określają dostęp innych klas do zmiennej członkowskiej. Aby uzyskać więcej informacji o określaniu dostępu, zobacz [Kontrola dostępu do elementów członkowskich](../cpp/member-access-control-cpp.md). Poziom dostępu do zmiennej składowej jest domyślnie ustawiony na wartość **`public`** .

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

- **Typ zmiennej**

  Ustawia zwracany typ dla zmiennej członkowskiej, która jest dodawana.

  - Jeśli dodajesz zmienną członkowską, która nie jest kontrolką okna dialogowego, wybierz z listy dostępnych typów.

    Aby uzyskać informacje o typach, zobacz [podstawowe typy](../cpp/fundamental-types-cpp.md).

    - **`char`**
    - **`double`**
    - **`float`**
    - **`int`**
    - **`long`**
    - **`short`**
    - **`unsigned char`**
    - **`unsigned int`**
    - **`unsigned long`**

  - Jeśli dodajesz zmienną członkowską dla kontrolki okna dialogowego, to pole jest wypełnione typem obiektu, który jest zwracany dla kontrolki lub wartości. W przypadku wybrania opcji **sterowanie**, a następnie **Typ zmiennej** określa klasę bazową kontrolki wybranej w polu **Identyfikator kontrolki** . Jeśli formant okna dialogowego może przechowywać wartość i w przypadku wybrania **wartości**, **Typ zmiennej** określa odpowiedni typ dla wartości, która może być przechowywana przez kontrolę. Aby uzyskać więcej informacji, zobacz [kontrolki okna dialogowego i typy zmiennych](#dialog-box-controls-and-variable-types).

    Ta wartość zależy od wyboru w **identyfikatorze kontrolki** i nie można jej zmienić.

- **Nazwa zmiennej**

  Ustawia nazwę dodawanej zmiennej członkowskiej. Zmienne składowe zwykle zaczynają się od ciągu identyfikacyjnego `m_` , który jest dostarczany domyślnie.

- **Zmienna sterująca**

  Wskazuje, że zmienna członkowska zarządza kontrolką w oknie dialogowym z obsługą [wymiany danych i sprawdzaniem poprawności danych](../mfc/dialog-data-exchange-and-validation.md) . Aby uzyskać więcej informacji, zobacz [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange). Ta opcja jest dostępna tylko dla zmiennych składowych dodanych do klas pochodnych z [CDialog](../mfc/reference/cdialog-class.md). Zaznacz to pole, aby uaktywnić opcje **sterowania identyfikatorem** i **typem formantu** .

- **Identyfikator kontrolki**

  Ustawia identyfikator dodawanej zmiennej kontrolki. Wybierz z listy Identyfikator typu kontrolki, do której dodawana jest zmienna elementu członkowskiego. Lista jest aktywna tylko wtedy, gdy pole **zmienna kontrolki** jest zaznaczone i jest ograniczone do identyfikatorów dla kontrolek, które zostały już dodane do okna dialogowego. Na przykład dla standardowego przycisku **OK** identyfikator kontrolki to **IDOK**.

  |Opcja|Opis|
  |------------|-----------------|
  |**Kontrola**|Ta opcja jest domyślnie ustawiona dla typu formantu. Zarządza nim sama kontrolka, a nie jego stan lub zawartość kontrolki (jak możesz chcieć zarządzać w przypadku pola listy, pola kombi lub pola edycji).|
  |**Wartość**|Ta opcja jest dostępna dla typów kontroli, które mogą przechowywać wartość lub pokazać stan, na przykład pole edycji lub pole wyboru. Jest ona również dostępna dla typów formantów, dla których można zarządzać zakresem, zawartością lub stanem. Aby uzyskać więcej informacji, zobacz [kontrolki okna dialogowego i typy zmiennych](#dialog-box-controls-and-variable-types).|

- **Kategoria**

  Określa, czy zmienna jest oparta na typie kontrolki, czy na wartości formantu.

- **Typ kontrolki**

  Ustawia typ kontrolki, która jest dodawana. To pole nie jest dostępne do zmiany. Na przykład przycisk ma **przycisk**typ kontrolki, a pole kombi ma typ kontrolki **ComboBox**. Aby uzyskać więcej informacji, zobacz [kontrolki okna dialogowego i typy zmiennych](#dialog-box-controls-and-variable-types).

- **Maksymalna liczba znaków**

  Dostępne tylko wtedy, gdy **zmienna Type** ma wartość [CString](../atl-mfc-shared/reference/cstringt-class.md). Wskazuje największą liczbę znaków, jaką może zawierać formant.

- **Wartość minimalna**

  Dostępne tylko wtedy, gdy zmienna Type ma wartość,,,,,,,,, `BOOL` **`int`** `UINT` **`long`** `DWORD` **`float`** **`double`** `BYTE` **`short`** [COLECurrency](../mfc/reference/colecurrency-class.md) lub [CTime](../atl-mfc-shared/reference/ctime-class.md). Wskazuje najniższą wartość akceptowalną dla skali lub zakresu dat.

- **Wartość maksymalna**

  Dostępne tylko wtedy, gdy zmienna Type ma wartość,,,,,,,,, `BOOL` **`int`** `UINT` **`long`** `DWORD` **`float`** **`double`** `BYTE` **`short`** `COLECurrency` lub `CTime` . Wskazuje największą wartość akceptowalną dla skali lub zakresu dat.

- **plik h**

  Dla kontrolek ActiveX, których zmienne składowe wymagają klasy otoki. Ustawia nazwę pliku nagłówkowego, aby dodać deklarację klasy.

- **plik. cpp**

  Dla kontrolek ActiveX, których zmienne składowe wymagają klasy otoki. Ustawia nazwę pliku implementacji, aby dodać definicję klasy.

- **Komentarz**

  Zawiera komentarz w pliku nagłówkowym dla zmiennej składowej.

## <a name="dialog-box-controls-and-variable-types"></a>Kontrolki okna dialogowego i typy zmiennych

Aby dodać zmienną członkowską do formantu okna dialogowego utworzonego za pomocą MFC, można użyć [Kreatora dodawania zmiennej członkowskiej](#add-member-variable-wizard) . Typ formantu, dla którego dodawana jest zmienna elementu członkowskiego określa opcje, które są wyświetlane w oknie dialogowym.

W poniższej tabeli opisano wszystkie typy formantów okna dialogowego, które są obsługiwane w MFC i [edytorze okien dialogowych](../windows/dialog-editor.md). Wyświetla także dostępne typy i wartości.

|Kontrola|Typ kontrolki|Typ zmiennej kontrolki|Typ zmiennej wartości|Wartości minimalne/maksymalne (tylko typ wartości)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|Kontrolka animacji|SysAnimate32|[Korzystanie CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Dawaj tylko kontrolka|Nie dotyczy|
|Przycisk|PRZYCISK|[CButton](../mfc/reference/cbutton-class.md)|Dawaj tylko kontrolka|Nie dotyczy|
|Pole wyboru|NIEZAZNACZONE|[CButton](../mfc/reference/cbutton-class.md)|`BOOL`|Wartość minimalna/maksymalna|
|Pole kombi|SKŁADNIK|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|Maksymalna liczba znaków|
|Kontrolka selektora daty i godziny|SysDateTimePick32|[Korzystanie CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|Wartość minimalna/maksymalna|
|Pole edycji|EDYTUJ|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, Long, DWORD, float, Double, BYTE, Short, BOOL, `COleDateTime` lub `COleCurrency`|Wartość minimalna/maksymalna wartość; Maksymalna liczba znaków w obsłudze|
|Klawisz skrótu|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Dawaj tylko kontrolka|Nie dotyczy|
|Pole listy|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|Maksymalna liczba znaków|
|Kontrolka listy|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|Dawaj tylko kontrolka|Nie dotyczy|
|Formant kalendarza miesięcznego|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Wartość minimalna/maksymalna|
|Kontrolka postępu|msctls_progress32|[Korzystanie CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Dawaj tylko kontrolka|Nie dotyczy|
|Kontrolka edycji wzbogaconej 2|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Maksymalna liczba znaków|
|Kontrolka edycji wzbogaconej|RICHEDIT|`CRichEditCtrl`|`CString`|Maksymalna liczba znaków|
|Pasek przewijania (w pionie lub w poziomie)|PASKI|[CScrollBar](../mfc/reference/cscrollbar-class.md)|**`int`**|Wartość minimalna/maksymalna|
|suwak|msctls_trackbar32|[Korzystanie CSliderCtrl](../mfc/reference/csliderctrl-class.md)|**`int`**|Wartość minimalna/maksymalna|
|Kontrolka pokrętła|msctls_updown32|[Korzystanie CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Dawaj tylko kontrolka|Nie dotyczy|
|Kontrolka karta|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Dawaj tylko kontrolka|Nie dotyczy|
|Kontrolka drzewa|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Dawaj tylko kontrolka|Nie dotyczy|
