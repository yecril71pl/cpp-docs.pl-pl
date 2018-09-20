---
title: Formatowanie obiektu CString i wyświetlanie okna komunikatu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.strings
dev_langs:
- C++
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 125d0d3ec1549b9eba46cbfebfb7ecfe2c2186d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387188"
---
# <a name="cstring-formatting-and-message-box-display"></a>Formatowanie obiektu CString i wyświetlanie okna komunikatu

Liczba funkcji są przekazywane do formatowania i analizowania `CString` obiektów. Tych funkcji można używać zawsze wtedy, gdy masz do manipulowania `CString` obiektów, ale są szczególnie przydatne do formatowania ciągów, które będą wyświetlane w oknie komunikatu tekstowego.

Ta grupa funkcji obejmuje również globalnego procedurę do wyświetlania okno komunikatu.

### <a name="cstring-functions"></a>Cstring — funkcje

|||
|-|-|
|[Afxextractsubstring —](#afxextractsubstring)|Wyodrębnianie podciągów rozdzielone pojedynczy znak w ciągu danego źródła.|
|[AfxFormatString1](#afxformatstring1)|Substytuty dany ciąg znaków formatu "%1" w ciągu zawartych w tablicy ciągów.|
|[AfxFormatString2](#afxformatstring2)|Substytuty dwa ciągi formatu znaków "%1" i "%2" w ciągu zawartych w tablicy ciągów.|
|[AfxMessageBox](#afxmessagebox)|Wyświetla okno komunikatu.|

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxextractsubstring"></a>  Afxextractsubstring —

Ta funkcja globalna może służyć do wyodrębniania podciągu z ciągu danego źródła.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do [CString](../../atl-mfc-shared/using-cstring.md) obiektu, który będą wysyłane poszczególne podciąg.

*lpszFullString*<br/>
Ciąg zawierający pełny tekst ciąg znaków do wyodrębnienia z.

*iSubString*<br/>
Liczony od zera indeks substring, wyodrębniania z *lpszFullString*.

*chSep*<br/>
Znak separatora, używana do ograniczania podciągów.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli funkcja pomyślnie wyodrębniany podciąg dla podanego indeksu; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatne w przypadku wyodrębnianych wiele podciągów w ciągu źródłowym, jeśli znane pojedynczy znak oddziela każdego podciągu. Ta funkcja przeszukuje od początku *lpszFullString* parametru każdym razem jest wywoływana.

Ta funkcja zwróci wartość FALSE, jeśli *lpszFullString* ma wartość NULL lub funkcja osiągnie koniec *lpszFullString* bez znajdowanie *iSubString*+ 1 wystąpienia określonego separatora. *RString* parametru nie zostaną zmodyfikowane od oryginalnej wartości, jeśli *lpszFullString* została ustawiona na wartość NULL; w przeciwnym razie *rString* parametr jest ustawiony na pusty ciąg, jeśli Nie można wyodrębnić podciąg dla określonego indeksu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxformatstring1"></a>  AfxFormatString1

Zastępuje ciąg wskazywany przez *lpsz1* dla wystąpienia "%1" dla znaków zasobu ciągu szablonu, które są identyfikowane za pomocą *nIDS*.

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do `CString` obiekt, który będzie zawierać wynikowy ciąg, po wykonaniu podstawienia.

*nIDS*<br/>
Identyfikator zasobu ciąg szablonu, na którym będą wykonywane podstawienia.

*lpsz1*<br/>
Ciąg, który zastąpi format znaków "%1" w parametrach szablonu.

### <a name="remarks"></a>Uwagi

Nowo utworzonej ciąg jest przechowywany w *rString*. Na przykład, jeśli ciąg w tabeli ciągów jest "Pliku" %1 nie można odnaleźć i *lpsz1* jest równa "C:\MYFILE. TXT", następnie *rString* będzie zawierać ciąg"plik C:\MYFILE. TXT nie można odnaleźć". Ta funkcja jest przydatna do formatowania ciągów wysyłane do okna komunikatów i innych oknach.

Jeśli formatowania znaków "%1" ma więcej niż jeden raz w ciągu, nastąpi wielu podstawienia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxformatstring2"></a>  AfxFormatString2

Zastępuje ciąg wskazywany przez *lpsz1* wszystkie wystąpienia znaków "%1" i ciągu wskazywany przez *lpsz2* dla wystąpienia "%2" dla znaków szablonu zasobu ciągu identyfikowane za pomocą *nIDS*.

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do `CString` , będzie zawierać wynikowy ciąg znaków, po wykonaniu podstawienia.

*nIDS*<br/>
Identyfikator tabeli ciągu ciąg szablonu, na którym będą wykonywane podstawienia.

*lpsz1*<br/>
Ciąg, który zastąpi format znaków "%1" w parametrach szablonu.

*lpsz2*<br/>
Ciąg, który zastąpi format znaków "%2" w parametrach szablonu.

### <a name="remarks"></a>Uwagi

Nowo utworzonej ciąg jest przechowywany w *rString*. Na przykład, jeśli ciąg w tabeli ciągów jest "Plik %1 nie został znaleziony w katalogu %2" *lpsz1* wskazuje "MYFILE. "TXT", a *lpsz2* wskazuje "C:\MYDIR", następnie *rString* będzie zawierać ciąg "plik MYFILE. Nie odnaleziono w katalogu C:\MYDIR TXT"

Jeśli format znaków "%1" lub "%2" wystąpić więcej niż jeden raz w ciągu, nastąpi wielu podstawienia. Nie muszą znajdować się w kolejności liczbowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxmessagebox"></a>  AfxMessageBox

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
Wskazuje `CString` obiekt lub ciąg przerwany wartością null, zawierający komunikat do wyświetlenia w oknie komunikatu.

*nNie*<br/>
Styl okna komunikatu. Zastosowania któregokolwiek z [Style okna komunikatu](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) do pola.

*nIDHelp*<br/>
Identyfikator kontekstu pomocy dla wiadomości; 0 wskazuje, że w kontekście pomocy domyślnej aplikacji będą używane.

*nIDPrompt*<br/>
Unikatowy identyfikator używany do odwoływania ciąg znaków w tablicy ciągów.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli nie ma wystarczającej ilości pamięci, aby wyświetlić okno komunikatu; w przeciwnym razie jest jedną z następujących wartości zwracane:

- Wybrano IDABORT przycisk Przerwij.

- Wybrano IDCANCEL przycisk Anuluj.

- IDIGNORE przycisk Ignoruj został wybrany.

- Przycisk IDNO nie został wybrany.

- Został wybrany przycisk IDOK OK.

- Wybrano IDRETRY przycisk Ponów próbę.

- IDYES został wybrany przycisk Tak.

Jeśli okno komunikatu ma przycisk Anuluj, zostanie zwrócona wartość IDCANCEL, jeśli zostanie naciśnięty klawisz ESC lub wybierze przycisk Anuluj. Jeśli okno komunikatu nie posiada przycisku Anuluj, naciskając klawisz ESC nie ma znaczenia.

Funkcje [AfxFormatString1](#afxformatstring1) i [AfxFormatString2](#afxformatstring2) mogą być przydatne do formatowania tekstu wyświetlanego w oknie komunikatu.

### <a name="remarks"></a>Uwagi

Pierwszy formularz tej przeciążonej funkcji wyświetla ciąg tekstowy wskazywany przez *lpszText* w oknie komunikatu i wykorzystuje *nIDHelp* do opisania kontekstu pomocy. Pomoc kontekstowa jest używana do przechodzenia do skojarzonego tematu pomocy, gdy użytkownik naciśnie klawisz Pomocy (zwykle F1).

Druga forma funkcji wykorzystuje zasoby ciągu z Identyfikatorem *nIDPrompt* Aby komunikat był wyświetlany w oknie komunikatu. Skojarzona strona pomocy zostanie znaleziona poprzez wartość *nIDHelp*. Jeśli wartość domyślną *nIDHelp* jest używana (-1), identyfikator ciągu zasobu *nIDPrompt*, jest używany w kontekście pomocy. Aby uzyskać więcej informacji dotyczących definiowania kontekstów pomocy, zobacz [Uwagi techniczne 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT, klasa](../../atl-mfc-shared/reference/cstringt-class.md)
