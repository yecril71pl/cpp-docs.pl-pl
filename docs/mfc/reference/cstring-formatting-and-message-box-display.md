---
title: Formatowanie obiektu CString i wyświetlanie okna komunikatu
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: d30d26ecf0e72ee33affe3df5b88c438ff83bb6b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365996"
---
# <a name="cstring-formatting-and-message-box-display"></a>Formatowanie obiektu CString i wyświetlanie okna komunikatu

Wiele funkcji są dostarczane do formatowania `CString` i analizowania obiektów. Te funkcje można używać zawsze, `CString` gdy trzeba manipulować obiektami, ale są one szczególnie przydatne do formatowania ciągów, które będą wyświetlane w tekście okna wiadomości.

Ta grupa funkcji zawiera również globalną procedurę wyświetlania okna komunikatu.

### <a name="cstring-functions"></a>Funkcje CString

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|Wyodrębnia podciągi oddzielone pojedynczym znakiem z danego ciągu źródłowego.|
|[AfxFormatString1](#afxformatstring1)|Zastępuje dany ciąg znaków formatu "%1" w ciągu zawartym w tabeli ciągów.|
|[AfxFormatString2](#afxformatstring2)|Zastępuje dwa ciągi znaków formatu "%1" i "%2" w ciągu zawartym w tabeli ciągów.|
|[Afxmessagebox](#afxmessagebox)|Wyświetla okno komunikatu.|

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxextractsubstring"></a><a name="afxextractsubstring"></a>AfxExtractSubString

Ta funkcja globalna może służyć do wyodrębniania podciągów z danego ciągu źródłowego.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do [CString](../../atl-mfc-shared/using-cstring.md) obiektu, który otrzyma pojedynczy podciąg.

*lpszFullString*<br/>
Ciąg zawierający pełny tekst ciągu do wyodrębnienia.

*ISubString (siekanie)*<br/>
Indeks zerowy podciągów do wyodrębnienia z *lpszFullString*.

*chSep (chSep)*<br/>
Znak separatora używany do rozdzielania podciągów.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli funkcja pomyślnie wyodrębniła podciąg w podanym indeksie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna do wyodrębniania wielu podciągów z ciągu źródłowego, gdy znany pojedynczy znak oddziela każdy podciąg. Ta funkcja wyszukuje od początku *parametru lpszFullString* za każdym razem, gdy jest wywoływana.

Ta funkcja zwróci FAŁSZ, jeśli *lpszFullString* jest ustawiona na NULL lub funkcja osiągnie koniec *lpszFullString* bez znajdowania wystąpień *iSubString*+1 określonego znaku separatora. Parametr *rString* nie zostanie zmodyfikowany z oryginalnej wartości, jeśli *lpszFullString* został ustawiony na NULL; w przeciwnym razie *rString* parametr jest ustawiony na pusty ciąg, jeśli nie można wyodrębnić podciąg dla określonego indeksu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxformatstring1"></a><a name="afxformatstring1"></a>AfxFormatString1

Zastępuje ciąg wskazany przez *lpsz1* dla wszelkich wystąpień znaków "%1" w zasobie ciągu szablonu identyfikowanym przez *nIDS*.

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do `CString` obiektu, który będzie zawierał wynikowy ciąg po wykonaniu podstawienia.

*nIDS (NIDS)*<br/>
Identyfikator zasobu ciągu szablonu, na którym zostanie wykonane podstawienie.

*lpsz1*<br/>
Ciąg, który zastąpi znaki formatu "%1" w ciągu szablonu.

### <a name="remarks"></a>Uwagi

Nowo utworzony ciąg jest przechowywany w *rString*. Na przykład, jeśli ciąg w tabeli ciągów jest "Plik %1 nie znaleziono", a *lpsz1* jest równa "C:\MYFILE. TXT", a następnie *rString* będzie zawierać ciąg "Plik C:\MYFILE. Nie znaleziono TXT". Ta funkcja jest przydatna do formatowania ciągów wysyłanych do skrzynek wiadomości i innych okien.

Jeśli znaki formatu "%1" pojawiają się w ciągu więcej niż jeden raz, zostanie dokonanych wiele podstawieńców.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxformatstring2"></a><a name="afxformatstring2"></a>AfxFormatString2

Zastępuje ciąg wskazany przez *lpsz1* dla wszelkich wystąpień znaków "%1", a ciąg wskazywał przez *lpsz2* dla wszelkich wystąpień znaków "%2", w zasobie ciągu szablonu identyfikowanym przez *nIDS*.

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do `CString` tego, który będzie zawierać wynikowy ciąg po wykonaniu podstawienia.

*nIDS (NIDS)*<br/>
Identyfikator tabeli ciągów ciągu ciągu ciągu, na którym zostanie wykonane podstawienie.

*lpsz1*<br/>
Ciąg, który zastąpi znaki formatu "%1" w ciągu szablonu.

*lpsz2*<br/>
Ciąg, który zastąpi znaki formatu "%2" w ciągu szablonu.

### <a name="remarks"></a>Uwagi

Nowo utworzony ciąg jest przechowywany w *rString*. Jeśli na przykład ciąg w tabeli ciągów to "Nie znaleziono pliku %1 w katalogu %2", *lpsz1* wskazuje na "MYFILE. TXT", a *lpsz2* wskazuje na "C:\MYDIR", a następnie *rString* będzie zawierał ciąg "File MYFILE. Nie znaleziono txt w katalogu C:\MYDIR"

Jeśli znaki formatu "%1" lub "%2" pojawiają się w ciągu więcej niż jeden raz, zostanie dokonanych wiele podstawień. Nie muszą być w porządku liczbowym.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxmessagebox"></a><a name="afxmessagebox"></a>Afxmessagebox

Wyświetla okno komunikatu na ekranie.

```
int AfxMessageBox(
    LPCTSTR lpszText,
    UINT nType = MB_OK,
    UINT nIDHelp = 0);

int AFXAPI AfxMessageBox(
    UINT nIDPrompt,
    UINT nType = MB_OK,
    UINT nIDHelp = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
Wskazuje obiekt `CString` lub ciąg zakończony wartością null zawierający komunikat, który ma być wyświetlany w oknie komunikatu.

*nTyp*<br/>
Styl okna komunikatu. Zastosuj dowolny ze [stylów pola wiadomości](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) do tego pola.

*nIDHelp (pomoc nID)*<br/>
Identyfikator kontekstu Pomocy dla wiadomości; 0 oznacza, że zostanie użyty domyślny kontekst Pomocy aplikacji.

*nIDPrompt ( nIDPrompt )*<br/>
Unikatowy identyfikator używany do odwoływania się do ciągu w tabeli ciągów.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli nie ma wystarczającej ilości pamięci, aby wyświetlić okno komunikatu; w przeciwnym razie zwracana jest jedna z następujących wartości:

- IDABORT Wybrano przycisk Przerwać.

- IDCANCEL Wybrano przycisk Anuluj.

- IDIGNORE Wybrano przycisk Ignoruj.

- IDNO Wybrano przycisk Brak.

- IDOK Wybrano przycisk OK.

- IDRETRY Wybrano przycisk Ponów próbę.

- IDYES Wybrano przycisk Tak.

Jeśli w oknie komunikatu znajduje się przycisk Anuluj, wartość IDCANCEL zostanie zwrócona, jeśli zostanie naciśnięty klawisz ESC lub wybrano przycisk Anuluj. Jeśli w oknie komunikatu nie ma przycisku Anuluj, naciśnięcie klawisza ESC nie ma wpływu.

Funkcje [AfxFormatString1](#afxformatstring1) i [AfxFormatString2](#afxformatstring2) mogą być przydatne w formatowaniu tekstu wyświetlanego w oknie komunikatu.

### <a name="remarks"></a>Uwagi

Pierwsza forma tej przeciążonej funkcji wyświetla ciąg tekstowy wskazywał *lpszText* w polu komunikatu i używa *nIDHelp* do opisania kontekstu Pomocy. Kontekst Pomocy jest używany do przechodzenia do skojarzonego tematu Pomocy, gdy użytkownik naciśnie klawisz Pomocy (zazwyczaj F1).

Druga forma funkcji używa zasobu ciągu o identyfikatorze *nIDPrompt* do wyświetlania komunikatu w oknie komunikatu. Skojarzona strona Pomocy znajduje się za pomocą wartości *nIDHelp*. Jeśli używana jest wartość domyślna *nIDHelp* (-1), identyfikator zasobu ciągu *nIDPrompt*jest używany w kontekście Pomocy. Aby uzyskać więcej informacji na temat definiowania kontekstów Pomocy, zobacz [Uwaga techniczna 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT, klasa](../../atl-mfc-shared/reference/cstringt-class.md)
