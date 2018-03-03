---
title: 'Tn026: procedury DDX i Ddv | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15c2309e8080892bdca2753c1ea6128ce419862f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026: procedury DDX i DDV
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga opisano wymiana danych okna dialogowego (DDX) i architektura sprawdzania poprawności (DDV) danych w oknie dialogowym. Opisuje również sposób zapisania procedury DDX_ lub DDV_ i jak można rozszerzyć ClassWizard do użycia z procedury.  
  
## <a name="overview-of-dialog-data-exchange"></a>Omówienie wymiana danych okna dialogowego  
 Kod w języku C++ są wykonywane wszystkie funkcje danych w oknie dialogowym. Nie ma żadnych specjalnych zasobów lub magic makra. Mechanizm to funkcja wirtualna, która zostanie zastąpiona w każdej klasy okien dialogowych, że jest wymiany danych okna dialogowego i sprawdzania poprawności. Zawsze znajduje się w tym formularzu:  
  
```  
void CMyDialog::DoDataExchange(CDataExchange* pDX)  
{  
    CDialog::DoDataExchange(pDX);
*// call base class  
 *//{{AFX_DATA_MAP(CMyDialog)  
 <data_exchange_function_call>  
 <data_validation_function_call> *//}}AFX_DATA_MAP  
}  
```  
  
 Komentarze AFX specjalny format Zezwalaj ClassWizard do lokalizowania i edytować kod w tej funkcji. Kod, który nie jest zgodny z ClassWizard powinny być umieszczone poza komentarze specjalny format.  
  
 W powyższym przykładzie < data_exchange_function_call > ma postać:  
  
```  
DDX_Custom(pDX,
    nIDC,
    field);
```  
  
 i < data_validation_function_call > jest opcjonalna i ma postać:  
  
```  
DDV_Custom(pDX,
    field, ...);
```  
  
 Więcej niż jedna para DDX_/DDV_ może być zawarta w każdym `DoDataExchange` funkcji.  
  
 Listę wszystkich procedury wymiany danych okna dialogowego i procedury walidacji danych okna dialogowego wyposażone w MFC, zobacz "afxdd_.h".  
  
 Dane okna dialogowego są właśnie tę: dane elementów członkowskich w **CMyDialog** klasy. Nie są przechowywane w struktury lub niczego podobne.  
  
## <a name="notes"></a>Uwagi  
 Mimo że nazywamy to "dane okna dialogowego" wszystkie funkcje są dostępne w dowolnej klasy pochodne `CWnd` i nie są ograniczone do tylko okien dialogowych.  
  
 Wartości początkowe dane są ustawione w Konstruktorze standard C++, zazwyczaj w bloku z `//{{AFX_DATA_INIT` i `//}}AFX_DATA_INIT` komentarze.  
  
 `CWnd::UpdateData`Operacja inicjowania i obsługi wokół wywołanie błędów `DoDataExchange`.  
  
 Możesz wywołać `CWnd::UpdateData` w dowolnym momencie przeprowadzić wymiany danych i weryfikacji. Domyślnie `UpdateData`(PRAWDA) jest wywoływana w domyślnym `CDialog::OnOK` obsługi i `UpdateData`(FALSE) jest wywoływana w domyślnym `CDialog::OnInitDialog`.  
  
 Procedura DDV_ natychmiast należy wykonać procedury DDX_ tego *pola*.  
  
## <a name="how-does-it-work"></a>Jak to działa  
 Nie trzeba zrozumieć następujące, aby można było używać okna dialogowego danych. Jednak zrozumienie, jak to działa w tle pomoże Ci zapisu własnej procedury weryfikacji lub programu exchange.  
  
 `DoDataExchange` Funkcja członkowska jest podobne jak w przypadku `Serialize` funkcji członkowskiej — jest odpowiedzialny za pobierania lub ustawiania danych do/z formularza zewnętrznych (w tym przypadku kontrolki w oknie dialogowym) od i do elementu członkowskiego danych w klasie. `pDX` Parametr kontekstu dla podczas wymiany danych i jest podobny do `CArchive` parametr `CObject::Serialize`. `pDX` ( `CDataExchange` Obiektu) ma kierunek Flaga wiele podobnych `CArchive` ma Flaga kierunku:  
  
-   Jeśli **! m_bSaveAndValidate**, następnie załadować stan danych do kontrolek.  
  
-   Jeśli `m_bSaveAndValidate`, następnie ustaw stan danych z kontrolki.  
  
 Sprawdzanie poprawności występuje tylko wtedy, gdy `m_bSaveAndValidate` jest ustawiona. Wartość `m_bSaveAndValidate` jest określana przez parametr BOOL `CWnd::UpdateData`.  
  
 Istnieją trzy inne interesujące `CDataExchange` członków:  
  
- `m_pDlgWnd`: Okno (zazwyczaj okna dialogowego), który zawiera formanty. Ma to zapobiec wywołań DDX_ i DDV_ funkcje globalne do przekazania "this" do każdej procedury DDX/ddv za.  
  
- `PrepareCtrl`, a `PrepareEditCtrl`: przygotowuje formantu okna dialogowego do wymiany danych. Przechowuje dojście tego formantu do ustawiania fokus, jeśli weryfikacja zakończy się niepowodzeniem. `PrepareCtrl`Służy do formantów nonedit i `PrepareEditCtrl` jest używany dla formantów edycyjnych.  
  
- **Niepowodzenie**: wywoływana po wykonaniu otworzeniem okna komunikatu alerty użytkownikowi błąd danych wejściowych. Ta procedura spowoduje przywrócenie fokus ostatniego formantu (ostatnie wywołanie `PrepareCtrl` / `PrepareEditCtrl`) i zgłosić wyjątek. Ta funkcja członkowska może być wywoływana z zarówno DDX_ i DDV_ procedury.  
  
## <a name="user-extensions"></a>Rozszerzenia użytkownika  
 Istnieje kilka sposobów, aby rozszerzyć domyślny mechanizm DDX/ddv za. Można:  
  
-   Dodaj nowe typy danych.  
  
 ```  
    CTime 
 ```  
  
-   Dodaj nowe procedury programu exchange (DDX_).  
  
 ```  
    void PASCAL DDX_Time(CDataExchange* pDX,
    int nIDC,
    CTime& tm);

 ```  
  
-   Dodaj nowe procedury weryfikacji (DDV_).  
  
 ```  
    void PASCAL DDV_TimeFuture(CDataExchange* pDX,
    CTime tm,
    BOOL bFuture);
*// make sure time is in the future or past  
 ```  
  
-   Przekazanie dowolnego wyrażenia do procedury weryfikacji.  
  
 ```  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxAge);

 ```  
  
    > [!NOTE]
    >  Takie dowolnego wyrażenia nie może być edytowany przez ClassWizard i powinna zostać przeniesiona poza komentarze specjalny format (/ / {{AFX_DATA_MAP(CMyClass)).  
  
 Ma **DoDialogExchange** funkcji członkowskiej obejmują warunków lub jakichkolwiek innych prawidłowy instrukcji C++ z mieszany — wymiana i Walidacja wywołania funkcji.  
  
```  
//{{AFX_DATA_MAP(CMyClass)  
DDX_Check(pDX,
    IDC_SEX,
    m_bFemale);

DDX_Text(pDX,
    IDC_EDIT1,
    m_age);

//}}AFX_DATA_MAP  
if (m_bFemale)  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxFemaleAge);

else  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxMaleAge);
```  
  
> [!NOTE]
>  Jak pokazano powyżej, taki kod nie może być edytowany przez ClassWizard i powinna być używana tylko poza komentarze specjalny format.  
  
## <a name="classwizard-support"></a>Obsługa ClassWizard  
 ClassWizard obsługuje DDX/ddv za dostosowań, umożliwiając integrację własnych procedur DDX_ i DDV_ ClassWizard interfejsu użytkownika. Jest to przydatne tylko kosztów Jeśli planujesz ponowne użycie określonej procedury DDX i DDV w projekcie lub w wielu projektach.  
  
 W tym celu specjalnego wpisów w DDX. CLW (poprzednie wersje programu Visual C++ przechowuje te informacje w APSTUDIO. INI) lub do projektu. Plik CLW. Specjalne wpisy mogą być wprowadzane w sekcji [ogólne informacje o] projektu. Plik CLW lub w sekcji [ExtraDDX] DDX. Plik CLW w katalogu \Program Files\Microsoft Visual Studio\Visual C ++ \bin. Może być konieczne utworzenie DDX. Plik CLW, jeśli jeszcze nie istnieje. Jeśli planujesz używać niestandardowe procedury DDX_/DDV_ tylko w niektórych projektach, należy dodać wpisów do sekcji [ogólne informacje o] projektu. CLW plików zamiast tego. Jeśli planujesz użyć procedury w wielu projektach, należy dodać wpisów do sekcji [ExtraDDX] DDX. CLW.  
  
 Te wpisy specjalne formatu jest:  
  
```  
ExtraDDXCount=n  
```  
  
 gdzie n to liczba wierszy ExtraDDX do wykonania  
  
```  
ExtraDDX=<keys>;<vb-keys>; <prompt>; <type>; <initValue>; <DDX_Proc>  
[;<DDV_Proc>; <prompt1>; <arg1>; [<prompt2>; <fmt2>]]  
```  
  
 gdzie jest numer 1 - n, wskazujące na liście, który jest definiowany typ DDX.  
  
 Każde pole jest rozdzielone znakiem ";". Poniżej opisano pola i ich przeznaczenie.  
  
 \<klucze >  
 = Lista pojedynczy znaki wskazujące, dla których formantów okna dialogowego ten typ zmiennej jest dozwolone.  
  
 E = edycji  
  
 C = dwustanowy pole wyboru  
  
 c = trzy stanowy pole wyboru  
  
 R = pierwszego przycisku radiowego w grupie  
  
 L = nonsorted listy  
  
 l = pole posortowanej listy  
  
 M = pola kombi (z edytowanie elementu)  
  
 N = lista rozwijana nonsorted  
  
 n = Lista rozwijana posortowana  
  
 1 = Jeśli DDX insert powinny zostać dodane do head listy (domyślny jest dodawany do fragmentu) to jest zazwyczaj używane do procedury DDX, związane z transferem właściwość 'Formantu'.  
  
 \<VB kluczy >  
 To pole jest używane tylko w produkcie 16-bitowego dla formantów VBX (VBX formanty nie są obsługiwane w produkcie 32-bitowe)  
  
 \<Wiersz >  
 Ciąg do umieszczenia w polu kombi właściwości (nie cudzysłowów)  
  
 \<Typ >  
 Pojedynczy identyfikator dla typu emitować w pliku nagłówka. W naszym przykładzie powyżej z DDX_Time to będzie miał ustawienie ctime —.  
  
 \<VB kluczy >  
 Nie jest używany w tej wersji i zawsze powinna być pusta  
  
 \<initValue >  
 Nieprawidłowa wartość — 0 lub pusty. Jeśli to pole jest puste, Brak wiersza inicjowania zostanie zapisany w sekcji //{{AFX_DATA_INIT pliku implementacji. Pusty wpis powinna być używana do obiektów C++ (takich jak `CString`, `CTime`i tak dalej), która ma konstruktorów zagwarantować poprawne zainicjowanie.  
  
 < DDX_Proc >  
 Pojedynczy identyfikator dla procedury DDX_. Nazwa funkcji C++ musi rozpoczynać się od "DDX_", ale nie zawiera identyfikatora < DDX_Proc > "DDX_". W powyższym przykładzie identyfikator < DDX_Proc > jest czas. Gdy ClassWizard zapisuje wywołanie funkcji w pliku implementacji w {{sekcji AFX_DATA_MAP go dołącza tę nazwę do DDX_, w związku z tym otrzymywanych DDX_Time.  
  
 \<komentarz >  
 Komentarz do wyświetlenia w oknie dialogowym dla zmiennej o tej DDX. Umieść tekst ma się tutaj i zwykle mają coś, który opisuje działania wykonywane przez pary DDX/ddv za.  
  
 < DDV_Proc >  
 DDV część wpis jest opcjonalny. Nie wszystkie procedury DDX mają odpowiednie procedury DDV. Często jest wygodniejsze do uwzględnienia w fazie weryfikacji w ramach transferu. To sytuacja często dotyczy z procedury DDV nie wymaga żadnych parametrów, ponieważ ClassWizard nie obsługuje procedur DDV bez żadnych parametrów.  
  
 \<ARG >  
 Pojedynczy identyfikator dla procedury DDV_. Nazwa funkcji C++ musi rozpoczynać się od "DDV_", ale nie dołączaj "DDX_" w identyfikatorze < DDX_Proc >.  
  
 następuje argumentów DDV 1 lub 2:  
  
 \<promptX >  
 ciąg, aby umieścić powyżej edytowanie elementu (z & dla akceleratora)  
  
 \<fmtX >  
 Format znak dla typu arg, jeden z  
  
 d = int  
  
 u = bez znaku  
  
 D = długi int (to znaczy, long)  
  
 U = long unsigned (to znaczy DWORD)  
  
 f = liczb zmiennoprzecinkowych  
  
 F = double  
  
 s = ciąg  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

