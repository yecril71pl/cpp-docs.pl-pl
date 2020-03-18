---
title: Formatowanie obiektu CString i wyświetlanie okna komunikatu
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: ad880c5302fd2274c5d46719e912461fd7497f10
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421129"
---
# <a name="cstring-formatting-and-message-box-display"></a>Formatowanie obiektu CString i wyświetlanie okna komunikatu

Do formatowania i analizowania obiektów `CString` są udostępniane różne funkcje. Tych funkcji można używać zawsze, gdy trzeba manipulować obiektami `CString`, ale są one szczególnie przydatne w przypadku formatowania ciągów, które pojawią się w tekście okna komunikatu.

Ta grupa funkcji zawiera również procedurę globalną do wyświetlania okna komunikatu.

### <a name="cstring-functions"></a>Funkcje CString

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|Wyodrębnia podciągi oddzielone pojedynczym znakiem z danego ciągu źródłowego.|
|[AfxFormatString1](#afxformatstring1)|Zastępuje dany ciąg znaków w formacie "%1" w ciągu zawartym w tabeli ciągów.|
|[AfxFormatString2](#afxformatstring2)|Zastępuje dwa ciągi znaków formatu "%1" i "%2" w ciągu zawartym w tabeli ciągów.|
|[AfxMessageBox](#afxmessagebox)|Wyświetla okno komunikatu.|

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxextractsubstring"></a>AfxExtractSubString

Ta funkcja globalna może służyć do wyodrębniania podciągu z danego ciągu źródłowego.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do obiektu [CString](../../atl-mfc-shared/using-cstring.md) , który będzie otrzymywał pojedynczy podciąg.

*lpszFullString*<br/>
Ciąg zawierający pełny tekst ciągu do wyodrębnienia.

*iSubString*<br/>
Indeks podciągu liczony od zera, który ma zostać wyodrębniony z *lpszFullString*.

*chSep*<br/>
Znak separatora używany do rozdzielania podciągów.

### <a name="return-value"></a>Wartość zwrócona

PRAWDA, jeśli funkcja pomyślnie wyodrębni podciąg z podanego indeksu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna do wyodrębniania wielu podciągów z ciągu źródłowego, gdy znany pojedynczy znak oddziela każdy podciąg. Ta funkcja wyszukuje od początku parametru *lpszFullString* przy każdym wywołaniu.

Ta funkcja zwróci wartość FALSE, jeśli właściwość *lpszFullString* ma wartość null lub funkcja osiągnie koniec *LpszFullString* bez wyszukiwania *iSubString*+ 1 wystąpień określonego znaku separatora. Parametr *rString* nie zostanie zmodyfikowany z oryginalnej wartości, jeśli wartość *lpszFullString* została ustawiona na null; w przeciwnym razie parametr *rString* jest ustawiany na pusty ciąg, jeśli podciąg nie może zostać wyodrębniony dla określonego indeksu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxformatstring1"></a>AfxFormatString1

Zastępuje ciąg wskazany przez *lpsz1* dla wszystkich wystąpień znaków "%1" w zasobie ciągu szablonu identyfikowanego przez *nIDS*.

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do obiektu `CString`, który będzie zawierać wynikowy ciąg po przeprowadzeniu podstawienia.

*nIDS*<br/>
Identyfikator zasobu ciągu szablonu, na którym zostanie wykonane podstawienie.

*lpsz1*<br/>
Ciąg, który zastąpi znaki formatu "%1" w ciągu szablonu.

### <a name="remarks"></a>Uwagi

Nowo utworzony ciąg jest przechowywany w *rString*. Na przykład jeśli ciąg w tabeli ciągów ma wartość "plik %1 nie został znaleziony", a *lpsz1* jest równa "C:\MYFILE. TXT ", a następnie *rString* będzie zawierać ciąg" File C:\MYFILE. Nie znaleziono TXT ". Ta funkcja jest przydatna w przypadku formatowania ciągów wysyłanych do pól komunikatów i innych okien.

Jeśli znaki w formacie "%1" pojawiają się w ciągu więcej niż raz, zostanie wykonane wiele podstawiania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxformatstring2"></a>AfxFormatString2

Zastępuje ciąg wskazany przez *lpsz1* dla wszystkich wystąpień znaków "%1" i ciąg wskazany przez *lpsz2* dla wszystkich wystąpień znaków "%2" w zasobie ciągu szablonu identyfikowanego przez *nIDS*.

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do `CString`, które będzie zawierać wynikowy ciąg po zakończeniu podstawiania.

*nIDS*<br/>
Identyfikator tabeli ciągów dla ciągu szablonu, na którym zostanie wykonane podstawienie.

*lpsz1*<br/>
Ciąg, który zastąpi znaki formatu "%1" w ciągu szablonu.

*lpsz2*<br/>
Ciąg, który zastąpi znaki formatu "%2" w ciągu szablonu.

### <a name="remarks"></a>Uwagi

Nowo utworzony ciąg jest przechowywany w *rString*. Na przykład jeśli ciąg w tabeli ciągów ma wartość "plik %1 nie został znaleziony w katalogu %2", *lpsz1* wskazuje na "mój plik. TXT "i *lpsz2* wskazuje na" C:\mydir ", a następnie *rString* będzie zawierać ciąg" plik. Nie znaleziono TXT w katalogu C:\MYDIR '

Jeśli znaki formatu "%1" lub "%2" pojawiają się w ciągu więcej niż raz, nastąpi przekroczenie wielu podstawiania. Nie muszą one być w kolejności liczbowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxmessagebox"></a>AfxMessageBox

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

*lpszText*<br/>
Wskazuje na obiekt `CString` lub ciąg zakończony znakiem null zawierający komunikat, który ma być wyświetlany w oknie komunikatu.

*Npowiadomienia*<br/>
Styl okna komunikatu. Zastosuj wszystkie [Style okna komunikatu](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) do pola.

*nIDHelp*<br/>
Identyfikator kontekstu pomocy dla wiadomości; 0 wskazuje, że domyślny kontekst pomocy aplikacji zostanie użyty.

*nIDPrompt*<br/>
Unikatowy identyfikator używany do odwoływania ciągu w tabeli ciągów.

### <a name="return-value"></a>Wartość zwrócona

Zero, jeśli nie ma wystarczającej ilości pamięci, aby wyświetlić okno komunikatu. w przeciwnym razie zwracana jest jedna z następujących wartości:

- IDABORT został wybrany przycisk Przerwij.

- IDCANCEL został wybrany przycisk Anuluj.

- IDIGNORE został wybrany przycisk Ignoruj.

- IDNO przycisk nie został wybrany.

- IDOK został wybrany przycisk OK.

- IDRETRY wybrano przycisk Ponów próbę.

- IDYES przycisk Tak.

Jeśli okno komunikatu ma przycisk Anuluj, wartość IDCANCEL będzie zwracana, jeśli klawisz ESC zostanie naciśnięty lub wybrano przycisk Anuluj. Jeśli okno komunikatu nie ma przycisku Anuluj, naciśnięcie klawisza ESC nie ma żadnego efektu.

Funkcje [AfxFormatString1](#afxformatstring1) i [AfxFormatString2](#afxformatstring2) mogą być przydatne w formatowaniu tekstu, który pojawia się w oknie komunikatu.

### <a name="remarks"></a>Uwagi

Pierwsza forma tej przeciążonej funkcji wyświetla ciąg tekstowy wskazywany przez *lpszText* w oknie komunikatu i używa *nIDHelp* do opisywania kontekstu pomocy. Kontekst pomocy służy do przechodzenia do skojarzonego tematu pomocy, gdy użytkownik naciśnie klawisz pomocy (zazwyczaj F1).

Druga forma funkcji używa zasobu ciągu o IDENTYFIKATORze *nIDPrompt* , aby wyświetlić komunikat w oknie komunikatu. Skojarzona Strona pomocy jest dostępna za pomocą wartości *nIDHelp*. Jeśli wartość domyślna *nIDHelp* jest używana (-1), identyfikator zasobu ciągu, *nIDPrompt*, jest używany dla kontekstu pomocy. Aby uzyskać więcej informacji o definiowaniu kontekstów pomocy, zobacz [Uwagi techniczne 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT, klasa](../../atl-mfc-shared/reference/cstringt-class.md)
