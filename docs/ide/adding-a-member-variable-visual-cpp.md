---
title: Dodaj zmienną składową
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
ms.openlocfilehash: 0f10b4867b443f0db69743d7ff23bb059290b0a5
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328964"
---
# <a name="add-a-member-variable"></a>Dodaj zmienną składową

Możesz dodać zmienną członkowską do klasy za pomocą widoku klas. Zmienne składowe mogą być albo dla [wymiany danych i sprawdzanie poprawności danych](../mfc/dialog-data-exchange-and-validation.md), lub może być ogólny. Kreator zmiennej elementu członkowskiego danych zaprojektowano podjąć odpowiednie informacje i użyć go do wstawienia elementów w plikach źródłowych w odpowiednich lokalizacjach. Możesz dodać zmienną członkowską z [Edytor okien dialogowych](../windows/dialog-editor.md) w [widok zasobów](../windows/how-to-create-a-resource-script-file.md#create-resources), lub z [Widok klas](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
> Podczas projektowania i implementowania okno dialogowe, może okazać się bardziej wydajne, można użyć okna dialogowego edytora, aby dodać formanty okna dialogowego, a następnie wdrożyć zmiennych składowych kontrolek.

**Aby dodać zmienną składową dla formantu w oknie dialogowym w widoku zasobów za pomocą Kreatora dodawania zmiennej składowej:**

1. W widoku zasobu rozwiń węzeł projektu i węzeł okna dialogowego, aby wyświetlić listę okien dialogowych projektu.

1. Dwukrotnie kliknij okno dialogowe, do którego chcesz dodać zmienną członkowską, aby otworzyć go w edytorze okien dialogowych.

1. W oknie dialogowym wyświetlany w edytorze okien dialogowych kliknij prawym przyciskiem myszy formant, do którego chcesz dodać zmienną członkowską.

1. W menu skrótów wybierz **Dodaj zmienną** do wyświetlenia [kreatora zmiennej elementu członkowskiego dodawania](#add-member-variable-wizard).

   > [!NOTE]
   > Wartość domyślna znajduje się już w **identyfikator formantu**.

1. Podaj informacje w polach odpowiedniego kreatora. Aby uzyskać więcej informacji, zobacz [formantów okna dialogowego i typy zmiennych](#dialog-box-controls-and-variable-types).

1. Wybierz **Zakończ** Dodaj definicję i implementację kodu do projektu i zamknąć kreatora.

**Aby dodać zmienną członkowską z widoku klasy za pomocą Kreatora dodawania zmiennej składowej:**

1. W [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), rozwiń węzeł projektu, aby wyświetlić klasy w projekcie.

1. Kliknij prawym przyciskiem myszy klasę, do której chcesz dodać zmienną.

1. W menu skrótów wybierz **Dodaj**, a następnie wybierz **Dodaj zmienną** wyświetlić Dodaj kreatora zmiennej elementu członkowskiego.

1. Podaj informacje w polach odpowiedniego kreatora. Aby uzyskać więcej informacji, zobacz [kreatora zmiennej elementu członkowskiego dodawania](#add-member-variable-wizard).

1. Wybierz **Zakończ** Dodaj definicję i implementację kodu do projektu i zamknąć kreatora.

## <a name="in-this-section"></a>W tej sekcji

- [Kreator dodawania zmiennej składowej](#add-member-variable-wizard)
- [Formanty okna dialogowego i typy zmiennych](#dialog-box-controls-and-variable-types)

## <a name="add-member-variable-wizard"></a>Kreator dodawania zmiennej składowej

Ten kreator dodaje deklaracji zmiennej składowej do pliku nagłówka. W zależności od opcji można dodać kod do pliku .cpp. Po dodaniu zmiennej składowej, za pomocą kreatora można edytować kod w środowisku programistycznym.

- **Dostęp**

  Ustawia dostęp do zmiennej elementu członkowskiego. Modyfikatory dostępu są słowami kluczowymi, określające dostęp, innych klas, że zmienna członka. Aby uzyskać więcej informacji na temat określania dostępu, zobacz [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md). Poziom dostępu do zmiennej elementu członkowskiego jest równa `public` domyślnie.

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

- **Typ zmiennej**

  Ustawia typ zwrotny dla zmiennej elementu członkowskiego, który dodajesz.

  - W przypadku dodawania zmiennej składowej, która nie jest kontrolka okna dialogowego, wybierz z listy dostępnych typów.

    Aby uzyskać informacje o typach, zobacz [podstawowych typów](../cpp/fundamental-types-cpp.md).

    |||
    |-|-|
    |`char`|`short`|
    |`double`|`unsigned char`|
    |`float`|`unsigned int`|
    |`int`|`unsigned long`|
    |`long`||

  - W przypadku dodawania zmiennej składowej formantu pola okna dialogowego, to pole jest wypełniane z typem obiektu, który jest zwracany w przypadku formantu lub wartość. Jeśli wybierzesz **kontroli**, następnie **typ zmiennej** Określa klasę bazową formantu wybierz w **identyfikator formantu** pole. Jeśli kontrolka okna dialogowego może zawierać wartości, a po wybraniu **wartość**, następnie **typ zmiennej** określa odpowiedni typ wartości, jaką może zawierać kontrolki. Aby uzyskać więcej informacji, zobacz [formantów okna dialogowego i typy zmiennych](#dialog-box-controls-and-variable-types).

    Ta wartość jest zależna od zaznaczenia w **identyfikator formantu** i nie można zmienić.

- **Nazwa zmiennej**

  Określa nazwę zmiennej elementu członkowskiego, który dodajesz. Zmienne członkowskie zwykle zaczyna się od ciągu identyfikujący `m_`, która domyślnie jest udostępniany dla Ciebie.

- **Zmienna sterująca**

  Wskazuje, że zmiennej składowej zarządza formantu w oknie dialogowym z [wymiany danych i sprawdzanie poprawności danych](../mfc/dialog-data-exchange-and-validation.md) pomocy technicznej. Aby uzyskać więcej informacji, zobacz [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange). Ta opcja jest dostępna tylko w przypadku zmienne Członkowskie dodane do klasy pochodne [CDialog](../mfc/reference/cdialog-class.md). Zaznacz to pole, aby aktywować **Identyfikator kontrolki** i **kontrolowanie typu** opcje.

- **Identyfikator formantu**

  Ustawia identyfikator dla zmiennej formantu dodawanego. Wybierz z listy identyfikator typu formantu, dla których w przypadku dodawania zmiennej składowej. Lista jest aktywny tylko wtedy, gdy **zmienna sterująca** pole jest zaznaczone, a jego dotyczy tylko identyfikatory dla formantów już dodana do okna dialogowego. Na przykład w przypadku standardowych **OK** jest identyfikator formantu przycisku **IDOK**.

  |Opcja|Opis|
  |------------|-----------------|
  |**Kontrolki**|Ta opcja jest ustawiona domyślnie dla kontrolek typu. Zarządza nim, nie stanu lub zawartość formantu (jak możesz zarządzać dla pola listy, pola kombi lub pola edycji).|
  |**Wartość**|Ta opcja jest dostępna dla typów formantów, które można przechowywać wartości lub wyświetlany jest stan, takich jak pole edycji lub okienka do zaznaczenia. Jest również dostępna dla typów formantów, dla których może zarządzać zakresu, zawartości lub stanu. Aby uzyskać więcej informacji, zobacz [formantów okna dialogowego i typy zmiennych](#dialog-box-controls-and-variable-types).|

- **Kategoria**

  Określa, czy zmienna jest oparta na typie kontrolki lub wartość formantu.

- **Typ formantu**

  Ustawia typ kontroli dodawany. To pole nie jest dostępna do zmiany. Na przykład przycisk ma typ formantu **przycisk**, i pole kombi typu formantu **COMBOBOX**. Aby uzyskać więcej informacji, zobacz [formantów okna dialogowego i typy zmiennych](#dialog-box-controls-and-variable-types).

- **Maksymalna liczba znaków**

  Dostępne tylko wtedy, gdy **typ zmiennej** ustawiono [CString](../atl-mfc-shared/reference/cstringt-class.md). Wskazuje największą liczbę znaków, które może zawierać kontrolki.

- **Wartość minimalna**

  Dostępne tylko wtedy, gdy typ zmiennej jest `BOOL`, `int`, `UINT`, `long`, `DWORD`, `float`, `double`, `BYTE`, `short`, [COLECurrency](../mfc/reference/colecurrency-class.md)lub [CTime](../atl-mfc-shared/reference/ctime-class.md). Wskazuje najniższej wartości dopuszczalne w zakresie skalowania lub daty.

- **Wartość maksymalna**

  Dostępne tylko wtedy, gdy typ zmiennej jest `BOOL`, `int`, `UINT`, `long`, `DWORD`, `float`, `double`, `BYTE`, `short`, `COLECurrency`, lub `CTime`. Wskazuje najwyższej wartości dopuszczalne w zakresie skalowania lub daty.

- **plik .h**

  Dla formantów ActiveX, których zmienne Członkowskie wymagają klasy otoki. Określa nazwę pliku nagłówka, aby dodać deklaracji klasy.

- **Plik CPP**

  Dla formantów ActiveX, których zmienne Członkowskie wymagają klasy otoki. Określa nazwę pliku implementacji, aby dodać definicję klasy.

- **Komentarz**

  Zawiera komentarz w pliku nagłówkowym zmiennej elementu członkowskiego.

## <a name="dialog-box-controls-and-variable-types"></a>Formanty okna dialogowego i typy zmiennych

Możesz użyć [Kreator dodawania zmiennej członkowskiej](#add-member-variable-wizard) można dodać zmiennej składowej do kontrolki pola dialogowe utworzone za pomocą MFC. Typ kontrolki, dla którego należy dodać zmiennej składowej Określa opcje, które są wyświetlane w oknie dialogowym.

W poniższej tabeli opisano wszystkie okna dialogowego pole typy formantów które są obsługiwane w MFC i [Edytor okien dialogowych](../windows/dialog-editor.md). Wyświetla również dostępne typy i wartości.

|formant|Typ formantu|Typ zmiennej sterującej|Typ zmiennej wartości|Minimalnej/maksymalnej wartości (tylko w przypadku typu wartości)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|Kontrolki animacji|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|None; tylko kontroli|Brak|
|Przycisk|PRZYCISK|[CButton](../mfc/reference/cbutton-class.md)|None; tylko kontroli|Brak|
|Pole wyboru|SPRAWDŹ|[CButton](../mfc/reference/cbutton-class.md)|`BOOL`|Minimalna wartość/maksymalna wartość|
|Pole kombi|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|Maksymalna liczba znaków|
|Kontrolka selektora czasu daty|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[Ctime —](../atl-mfc-shared/reference/ctime-class.md)|Minimalna wartość/maksymalna wartość|
|Pole edycji|EDYTUJ|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime`, lub `COleCurrency`|Minimalna wartość/maksymalna wartość; Niektóre znaki max pomocy technicznej|
|Kontrola skrótu|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|None; tylko kontroli|Brak|
|Pole listy|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|Maksymalna liczba znaków|
|Kontrolka listy|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|None; tylko kontroli|Brak|
|Kontrolowanie kalendarza miesięcznego|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Minimalna wartość/maksymalna wartość|
|Kontrolki postępu|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|None; tylko kontroli|Brak|
|Kontrolka 2 edycji wzbogaconej|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Maksymalna liczba znaków|
|Formantu edycji wzbogaconej|RICHEDIT|`CRichEditCtrl`|`CString`|Maksymalna liczba znaków|
|Pasek przewijania (poziomy lub pionowy|PASEK PRZEWIJANIA|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|Minimalna wartość/maksymalna wartość|
|suwak|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|Minimalna wartość/maksymalna wartość|
|Kontrolki pokrętła|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|None; tylko kontroli|Brak|
|Kontrolki karty|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|None; tylko kontroli|Brak|
|Kontrolka drzewa|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|None; tylko kontroli|Brak|
