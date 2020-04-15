---
title: 'TN026: procedury DDX i DDV'
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 711d433b51ca09836f372d09a11f86c28b82cce6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370346"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026: procedury DDX i DDV

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

W tej notatce opisano architekturę wymiany danych dialogowych (DDX) i sprawdzanie poprawności danych okna dialogowego (DDV). Opisano w nim również sposób pisania procedury DDX_ lub DDV_ oraz sposób rozszerzania programu ClassWizard w celu korzystania z procedur.

## <a name="overview-of-dialog-data-exchange"></a>Omówienie programu Dialog Data Exchange

Wszystkie funkcje danych okna dialogowego są wykonywane za pomocą kodu C++. Nie ma specjalnych zasobów ani magicznych makr. Sercem mechanizmu jest funkcja wirtualna, która jest zastępowane w każdej klasie okna dialogowego, która nie wymiany danych okna dialogowego i sprawdzania poprawności. Zawsze znajduje się w tej formie:

```cpp
void CMyDialog::DoDataExchange(CDataExchange* pDX)
{
    CDialog::DoDataExchange(pDX);   // call base class

    //{{AFX_DATA_MAP(CMyDialog)
        <data_exchange_function_call>
        <data_validation_function_call>
    //}}AFX_DATA_MAP
}
```

Specjalny format AFX komentarze pozwalają ClassWizard zlokalizować i edytować kod w ramach tej funkcji. Kod, który nie jest zgodny z ClassWizard powinny być umieszczone poza komentarze formatu specjalnego.

W powyższym \<przykładzie data_exchange_function_call> jest w formie:

```cpp
DDX_Custom(pDX, nIDC, field);
```

i \<data_validation_function_call> jest opcjonalna i ma formę:

```cpp
DDV_Custom(pDX, field, ...);
```

W każdej `DoDataExchange` funkcji może znajdować się więcej niż jedna para DDX_/DDV_.

Zobacz "afxdd_.h", aby uzyskać listę wszystkich procedur wymiany danych w oknie dialogowym i procedur sprawdzania poprawności danych okna dialogowego dostarczonych z MFC.

Dane okna dialogowego jest tylko, że: dane elementu członkowskiego w `CMyDialog` klasie. Nie jest przechowywany w strukturze lub coś podobnego.

## <a name="notes"></a>Uwagi

Chociaż nazywamy to "dane okna dialogowego", wszystkie `CWnd` funkcje są dostępne w dowolnej klasie pochodzące z i nie są ograniczone tylko do okien dialogowych.

Początkowe wartości danych są ustawiane w standardowym konstruktorze C++, zwykle w bloku z `//{{AFX_DATA_INIT` i `//}}AFX_DATA_INIT` komentarze.

`CWnd::UpdateData`jest operacją, która wykonuje inicjowanie `DoDataExchange`i obsługę błędów wokół wywołania .

Można wywołać `CWnd::UpdateData` w dowolnym momencie do wykonywania wymiany danych i sprawdzania poprawności. Domyślnie `UpdateData`(PRAWDA) jest wywoływana w domyślnym `CDialog::OnOK` programie obsługi i `UpdateData`(FALSE) jest wywoływana domyślnie `CDialog::OnInitDialog`.

Procedura DDV_ powinna natychmiast postępować zgodnie z DDX_ procedurą dla tego *pola.*

## <a name="how-does-it-work"></a>Jak to działa

Aby użyć danych okna dialogowego, nie trzeba rozumieć następujących elementów. Jednak zrozumienie, jak to działa za kulisami pomoże Ci napisać własną procedurę wymiany lub sprawdzania poprawności.

Funkcja `DoDataExchange` elementu członkowskiego jest `Serialize` podobnie jak funkcja elementu członkowskiego — jest odpowiedzialna za pobieranie lub ustawianie danych do/z formularza zewnętrznego (w tym przypadku formantów w oknie dialogowym) z/do danych członkowskich w klasie. Parametr *pDX* jest kontekstem wymiany danych i `CArchive` jest `CObject::Serialize`podobny do parametru do . *PDX* `CDataExchange` (obiekt) ma flagę kierunku `CArchive` podobnie jak ma flagę kierunku:

- Jeśli `!m_bSaveAndValidate`, a następnie załadować stan danych do formantów.

- Jeśli `m_bSaveAndValidate`, a następnie ustawić stan danych z formantów.

Sprawdzanie poprawności `m_bSaveAndValidate` występuje tylko wtedy, gdy jest ustawiona. Wartość `m_bSaveAndValidate` jest określana przez parametr `CWnd::UpdateData`BOOL do .

Istnieje trzy inne `CDataExchange` interesujące członków:

- `m_pDlgWnd`: Okno (zwykle okno dialogowe zawierające formanty. Ma to zapobiec wywołujących DDX_ i DDV_ funkcje globalne z konieczności przekazywania "to" do każdej procedury DDX /DDV.

- `PrepareCtrl`i `PrepareEditCtrl`: Przygotowuje kontrolkę okna dialogowego do wymiany danych. Przechowuje dojście tego formantu do ustawiania fokusu, jeśli sprawdzanie poprawności nie powiedzie się. `PrepareCtrl`jest używany do formantów nieedytów i `PrepareEditCtrl` jest używany do edycji formantów.

- `Fail`: Wywoływane po wywołaniu okna komunikatu ostrzegającego użytkownika o błędzie wejściowym. Ta procedura przywróci fokus do ostatniego `PrepareCtrl` formantu (ostatnie wywołanie lub) `PrepareEditCtrl`i zda wyjątek. Ta funkcja elementu członkowskiego może być wywoływana zarówno z procedur DDX_, jak i DDV_.

## <a name="user-extensions"></a>Rozszerzenia użytkownika

Istnieje kilka sposobów rozszerzenia domyślnego mechanizmu DDX/DDV. Możesz:

- Dodaj nowe typy danych.

    ```cpp
    CTime
    ```

- Dodaj nowe procedury wymiany (DDX_).

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- Dodaj nowe procedury sprawdzania poprawności (DDV_).

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- Przekazywanie dowolnych wyrażeń do procedur sprawdzania poprawności.

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > Takie dowolne wyrażenia nie mogą być edytowane przez ClassWizard i dlatego powinny zostać przeniesione poza komentarze w formacie specjalnym (//{{AFX_DATA_MAP(CMyClass)).

Czy `DoDialogExchange` funkcja elementu członkowskiego zawiera warunki lub inne prawidłowe instrukcje C++ z wywołaniami funkcji wymiany i sprawdzania poprawności.

```cpp
//{{AFX_DATA_MAP(CMyClass)
DDX_Check(pDX, IDC_SEX, m_bFemale);
DDX_Text(pDX, IDC_EDIT1, m_age);
//}}AFX_DATA_MAP
if (m_bFemale)
    DDV_MinMax(pDX, age, 0, m_maxFemaleAge);
else
    DDV_MinMax(pDX, age, 0, m_maxMaleAge);
```

> [!NOTE]
> Jak pokazano powyżej, taki kod nie może być edytowany przez ClassWizard i powinien być używany tylko poza specjalnymi komentarzami formatu.

## <a name="classwizard-support"></a>Pomoc techniczna w kreatorze

ClassWizard obsługuje podzbiór dostosowań DDX/DDV, umożliwiając zintegrowanie własnych DDX_ i DDV_ procedur z interfejsem użytkownika ClassWizard. W ten sposób jest tylko korzystne koszty, jeśli planujesz ponownie użyć poszczególnych procedur DDX i DDV w projekcie lub w wielu projektach.

Aby to zrobić, specjalne wpisy są dokonywane w DDX. CLW (poprzednie wersje programu Visual C++ przechowywali te informacje w programie APSTUDIO. INI) lub w projekcie . clw. Specjalne wpisy można wpisać w sekcji [Informacje ogólne] projektu . clw lub w sekcji [ExtraDDX] ddx. CLW w katalogu \Program Files\Microsoft Visual Studio\Visual C++\bin. Może być konieczne utworzenie DDX. CLW, jeśli jeszcze nie istnieje. Jeśli zamierzasz używać niestandardowych procedur DDX_/DDV_ tylko w określonym projekcie, dodaj je do sekcji [Informacje ogólne] projektu . zamiast tego plik CLW. Jeśli planujesz używać procedur w wielu projektach, dodaj wpisy do sekcji [ExtraDDX] DDX. Clw.

Ogólny format tych specjalnych wpisów jest:

> ExtraDDXCount =*n*

gdzie *n* jest liczba ExtraDDX? linii do naśladowania, z formularza

> ExtraDDX?=*klawisze*; *klawisze vb*; *monit*; *typ;* *initValue*; *DDX_Proc* [; *DDV_Proc*; *prompt1*; *arg1* [; *prompt2*; *fmt2*]]

Gdzie? jest liczbą 1 - *n* wskazującą, który typ DDX na liście, która jest definiowana.

Każde pole jest rozdzielone znakiem ";". Pola i ich przeznaczenie są opisane poniżej.

- *keys*

  Lista pojedynczych znaków wskazujących, dla którego okna dialogowego steruje tym typem zmiennej, jest dozwolona.

  |Znak|Dozwolona kontrola|
  |-|-|
  E | edytuj
  C | dwustanowe pole wyboru
  c | pole wyboru trójstanowe
  R | pierwszy przycisk radiowy w grupie
  L | niesortowane pole listy
  l | posortowane pole listy
  M | pole kombi (z elementem edycji)
  Nie | niesortowana lista upuszczania
  n | posortowana lista upuszczania
  1 | jeśli wstawić DDX powinny być dodawane do head of list (domyślnie jest dodać do ogona) Jest to zwykle używane dla procedur DDX, które przenoszą "Control" właściwość.

- *klawisze vb*

  To pole jest używane tylko w produkcie 16-bitowym dla formantów VBX (kontrolki VBX nie są obsługiwane w produkcie 32-bitowym)

- *Wierszu*

  Ciąg do umieszczenia w polu kombi właściwości (bez cudzysłowów)

- *Typu*

  Pojedynczy identyfikator typu do emisji w pliku nagłówka. W naszym powyższym przykładzie z DDX_Time, byłoby to ustawione na CTime.

- *klawisze vb*

  Nie używane w tej wersji i zawsze powinny być puste

- *initValue (initValue)*

  Wartość początkowa — 0 lub pusta. Jeśli jest pusty, w sekcji //{{AFX_DATA_INIT pliku implementacji nie zostanie zapisany żaden wiersz inicjowania. Pusty wpis powinien być używany dla obiektów `CString`Języka `CTime`C++ (takich jak , i tak dalej), które mają konstruktory, które gwarantują poprawne inicjowanie.

- *DDX_Proc*

  Pojedynczy identyfikator procedury DDX_. Nazwa funkcji C++ musi zaczynać się od "DDX_", ale nie zawiera "DDX_" w identyfikatorze \<> DDX_Proc. W powyższym przykładzie identyfikatorem \<DDX_Proc> będzie Time. Gdy ClassWizard zapisuje wywołanie funkcji do pliku implementacji w sekcji {{AFX_DATA_MAP, dołącza tę nazwę do DDX_, docierając w ten sposób do DDX_Time.

- *Komentarz*

  Komentarz, aby pokazać w oknie dialogowym dla zmiennej z tym DDX. Umieść w tym miejscu dowolny tekst i zwykle podaj coś opisującego operację wykonanę przez parę DDX/DDV.

- *DDV_Proc*

  Część DDV wpisu jest opcjonalna. Nie wszystkie procedury DDX mają odpowiednie procedury DDV. Często wygodniej jest uwzględnić fazę sprawdzania poprawności jako integralną część transferu. Często dzieje się tak, gdy procedura DDV nie wymaga żadnych parametrów, ponieważ ClassWizard nie obsługuje procedur DDV bez żadnych parametrów.

- *Arg*

  Pojedynczy identyfikator procedury DDV_. Nazwa funkcji C++ musi zaczynać się od "DDV_", ale nie zawiera \<"DDX_" w identyfikatorze> DDX_Proc.

  *arg* następuje 1 lub 2 args DDV:

  - *promptN*

      Ciąg, aby umieścić nad elementem edycji (z & dla akceleratora).

  - *fmtN ( fmtN )*

      Formatuj znak typu arg, jeden z:

      |Znak|Typ|
      |-|-|
      |d | int|
      |u | unsigned int|
      |D | long int (czyli długo)|
      |U | długo niepodpisany (czyli DWORD)|
      |k | float|
      |F | double|
      |s | ciąg|

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
