---
title: 'Tn026: procedury DDX i Ddv | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DDX
- DDV
dev_langs:
- C++
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18377d423ab150773ef5438f39c8e74914b5c425
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317423"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026: procedury DDX i DDV

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje wymiana danych okna dialogowego (DDX) i architektura sprawdzania poprawności (DDV) danych okna dialogowego. Opisano również sposób zapisu funkcje DDX_ lub DDV_ procedury i jak można je rozszerzyć ClassWizard do użycia z procedur.

## <a name="overview-of-dialog-data-exchange"></a>Omówienie wymiana danych okna dialogowego

Wszystkie funkcje danych w oknie dialogowym są wykonywane przy użyciu kodu w języku C++. Nie istnieją żadne specjalne zasoby ani magic makra. Serce mechanizmu to funkcja wirtualna, która została zastąpiona w każdej klasy okien dialogowych, że jest wymiany danych okna dialogowego i sprawdzania poprawności. Zawsze znajduje się w tym formularzu:

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

Komentarze AFX specjalny format umożliwiają ClassWizard zlokalizować i edytować kod w ramach tej funkcji. Kod, który nie jest zgodny z ClassWizard powinna znajdować się poza komentarze specjalny format.

W powyższym przykładzie \<data_exchange_function_call > ma postać:

```cpp
DDX_Custom(pDX, nIDC, field);
```

i \<data_validation_function_call > jest opcjonalny, a ma postać:

```cpp
DDV_Custom(pDX, field, ...);
```

Więcej niż jedną parę funkcje DDX_/DDV_ mogą zostać zawarte w każdej `DoDataExchange` funkcji.

Aby uzyskać listę wszystkich procedury wymiany danych okna dialogowego i procedury walidacji danych okna dialogowego wyposażone w MFC, zobacz "afxdd_.h".

Danych w oknie dialogowym jest po prostu: dane elementów członkowskich w `CMyDialog` klasy. Nie są przechowywane w struktury lub czymkolwiek, które są podobne.

## <a name="notes"></a>Uwagi

Mimo że nazywamy to "dane okna dialogowego", wszystkie funkcje są dostępne w dowolnej klasie pochodnej `CWnd` i nie są ograniczone do kilka okien dialogowych.

Początkowe wartości danych są ustawiane w Konstruktorze standard C++, zazwyczaj w bloku z `//{{AFX_DATA_INIT` i `//}}AFX_DATA_INIT` komentarzy.

`CWnd::UpdateData` Operacja inicjowania i obsługi wokół wywołania błędów `DoDataExchange`.

Możesz wywołać `CWnd::UpdateData` w dowolnym momencie przeprowadzić wymiany danych i sprawdzania poprawności. Domyślnie `UpdateData`(PRAWDA) jest wywoływana w domyślnym `CDialog::OnOK` obsługi i `UpdateData`(FALSE) jest wywoływana w domyślnym `CDialog::OnInitDialog`.

Procedura DDV_ natychmiast należy wykonać procedury funkcje DDX_ tego *pola*.

## <a name="how-does-it-work"></a>Jak to działa

Nie musisz zrozumieć następujące czynności, aby można było używać danych w oknie dialogowym. Jednak zrozumienie, jak to działa w tle są pomocne podczas pisania własnej procedury wymiany lub sprawdzania poprawności.

`DoDataExchange` Funkcja członkowska jest podobne do `Serialize` funkcji składowej — odpowiada za pobieranie lub ustawianie danych, do/z formularza zewnętrznych (w tym przypadku formantów w oknie dialogowym) od i do dane elementu członkowskiego w klasie. *PDX* parametr kontekstu do wykonywania wymiany danych i jest podobna do `CArchive` parametr `CObject::Serialize`. *PDX* ( `CDataExchange` obiekt) ma kierunek z flagą wiele podobnych `CArchive` Flaga kierunku:

- Jeśli `!m_bSaveAndValidate`, następnie załadować stan danych do kontrolek.

- Jeśli `m_bSaveAndValidate`, następnie ustawić stan danych w kontrolkach.

Sprawdzanie poprawności występuje tylko wtedy, gdy `m_bSaveAndValidate` jest ustawiona. Wartość `m_bSaveAndValidate` jest określana przez parametr BOOL `CWnd::UpdateData`.

Istnieją trzy inne interesujące `CDataExchange` elementy członkowskie:

- `m_pDlgWnd`: Okno (zazwyczaj okna dialogowego), który zawiera formanty. Ten parametr zapobiega obiektów wywołujących funkcje globalne funkcje DDX_ i DDV_ z konieczności "this" Przekaż do każdej procedury DDX/DDV.

- `PrepareCtrl`, a `PrepareEditCtrl`: przygotowuje formantu w oknie dialogowym wymianę danych. Przechowuje dojście tej kontrolki do ustawiania fokus, jeśli weryfikacja zakończy się niepowodzeniem. `PrepareCtrl` Służy do kontrolek bez edycji i `PrepareEditCtrl` służy do kontrolki edycji.

- `Fail`: Wywoływane po wprowadzeniu okno komunikatu, alerty użytkownikowi błąd danych wejściowych. Ta procedura spowoduje przywrócenie fokus do ostatniej kontroli (ostatnie wywołanie elementu `PrepareCtrl` lub `PrepareEditCtrl`) i zgłosić wyjątek. Ta funkcja elementu członkowskiego, może być wywoływana z funkcje DDX_ i DDV_ procedury.

## <a name="user-extensions"></a>Rozszerzenia dla użytkowników

Istnieje kilka sposobów, aby rozszerzyć domyślnego mechanizmu DDX/DDV. Można:

- Dodaj nowe typy danych.

    ```cpp
    CTime
    ```

- Dodaj nowe procedury wymiany (funkcje DDX_).

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- Dodaj nowe procedury weryfikacji (DDV_).

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- Przekaż dowolnego wyrażenia do procedur weryfikacji.

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > Takie dowolnego wyrażenia nie może być przez nich edytowane ClassWizard i powinna zostać przeniesiona poza komentarze specjalny format (/ / {{AFX_DATA_MAP(CMyClass)).

Masz `DoDialogExchange` funkcja elementu członkowskiego obejmują warunkowych lub jakichkolwiek innych prawidłowe instrukcji języka C++ z mieszany — wymiana i Walidacja wywołania funkcji.

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
> Jak wspomniano powyżej, taki kod nie może być przez nich edytowane ClassWizard i powinny być używane wyłącznie poza komentarze specjalny format.

## <a name="classwizard-support"></a>Obsługa ClassWizard

ClassWizard obsługuje podzbiór DDX/DDV dostosowań, umożliwiając Zintegruj swoje własne funkcje DDX_ i DDV_ procedury ClassWizard interfejsu użytkownika. W ten sposób jest jedynym kosztem korzystne, jeśli planujesz ponowne użycie określonej procedury DDX i DDV w projekcie lub w wielu projektach.

W tym celu specjalnego wpisów w DDX. CLW (poprzedniej wersji programu Visual C++ przechowuje te informacje w APSTUDIO. INI) lub w twoim projekcie. Plik CLW. Specjalne wpisy mogą być wprowadzane w [ogólne informacje o] części projektu. Plik CLW lub znajduje się w sekcji [ExtraDDX] DDX. CLW plik w katalogu \Program Files\Microsoft Visual Studio\Visual C ++ \bin. Może być konieczne utworzenie DDX. Plik CLW, jeśli jeszcze nie istnieje. Jeśli planujesz niestandardowe procedury funkcje DDX_/DDV_ należy używać tylko w niektórych projektów, należy dodać wpisy do [ogólne informacje o] części projektu. Zamiast tego z pliku CLW. Jeśli planujesz użyć procedur na wiele projektów, należy dodać wpisy do sekcji [ExtraDDX] DDX. CLW.

Ogólny format te wpisy specjalne to:

> ExtraDDXCount =*n*

gdzie *n* jest liczba ExtraDDX? wiersze z formularza

> ExtraDDX? =*klucze*; *klucze vb*; *wiersza*; *typu*; *initValue*; *DDX_Proc* [; *DDV_Proc*; *prompt1*; *arg1* [; *prompt2*; *fmt2*]]

gdzie? to numer 1 - *n* wskazująca, jakiego typu DDX na liście, który jest definiowany.

Każde pole jest rozdzielone znakiem ";". Pola i ich celem są opisane poniżej.

- *klucze*

  Lista pojedyncze znaki wskazujące dla formantów okna dialogowego, które ten typ zmiennej jest dozwolone.

  |Znak|Dozwolone kontroli|
  |-|-|
  E | Edytuj
  C | pole wyboru dwoma stanami
  c | pole wyboru trzy-stanowy
  R | pierwszy przycisk radiowy w grupie
  L | pole listy nonsorted
  l | okno w posortowanej listy
  M | pole kombi (z elementem edycji)
  N | Lista rozwijana nonsorted
  n | Lista rozwijana posortowany
  1 | Jeśli wstawianie DDX powinny zostać dodane do głowy listy (domyślny jest dodawany do tail) to jest zazwyczaj używana do procedury DDX, związane z transferem właściwość "Control".

- *klucze VB*

  To pole jest używane tylko w produkcie 16-bitowych dla formantów VBX (VBX formanty nie są obsługiwane w 32-bitowy produkt)

- *wiersz*

  Ciąg do umieszczenia w polu kombi właściwości (nie cudzysłowu)

- *Typ*

  Pojedynczy identyfikator typu do emitowania w pliku nagłówkowym. W naszym powyższym przykładzie za pomocą DDX_Time to będzie miał ustawienie CTime.

- *klucze VB*

  Nie jest używana w tej wersji i powinien zawsze być pusty

- *initValue*

  Początkowa wartość — 0 lub puste. Jeśli to pole jest puste, Brak wiersza inicjowania zostanie zapisany w sekcji //{{AFX_DATA_INIT pliku implementacji. Pusty element powinien być używany dla obiektów C++ (takie jak `CString`, `CTime`i tak dalej), które mają konstruktory, które gwarantują poprawne inicjowania.

- *DDX_Proc*

  Pojedynczy identyfikator procedury funkcje DDX_. Nazwa funkcji języka C++, musi rozpoczynać się od "Funkcje DDX_", ale nie dołączaj "Funkcje DDX_" \<DDX_Proc > identyfikator. W powyższym przykładzie \<DDX_Proc > Identyfikator byłoby czasu. Gdy ClassWizard zapisuje wywołania funkcji w pliku implementacji w {{sekcji AFX_DATA_MAP go dołącza tę nazwę do funkcje DDX_, w związku z tym otrzymywanych DDX_Time.

- *Komentarz*

  Komentarz do wyświetlenia w oknie dialogowym dla zmiennej za pomocą tego DDX. Umieść tutaj i zwykle zapewniają coś, co chcesz tekst, który opisuje operacji wykonywanych przez parę DDX/DDV.

- *DDV_Proc*

  DDV część wpis jest opcjonalny. Nie wszystkie procedury DDX mają odpowiednie procedury DDV. Często jest bardziej wygodne do uwzględnienia w fazie weryfikacji w ramach transferu. To sytuacja często dotyczy gdy Twoja procedura DDV nie wymaga żadnych parametrów, ponieważ ClassWizard nie obsługuje procedur DDV bez żadnych parametrów.

- *ARG*

  Pojedynczy identyfikator procedury DDV_. Nazwa funkcji języka C++ musi rozpoczynać się od "DDV_", ale nie powinno obejmować "Funkcje DDX_" \<DDX_Proc > identyfikator.

  *ARG* następuje args DDV 1 lub 2:

   - *promptN*

     Ciąg, który można umieścić powyżej edytowanie elementu (& dla akceleratora).

   - *fmtN*

     Formatem znaku typu arg, jeden z:

     |Znak|Typ|
     |-|-|
     d | int
     u | unsigned int
     D | long int (to znaczy, długi)
     U | czas bez znaku (czyli DWORD)
     f | float
     F | double
     s | string

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)  
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)  
