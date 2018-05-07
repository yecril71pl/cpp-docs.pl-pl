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
ms.openlocfilehash: 8074d84d739b59acfa0c6040bedf76f46b6ea9c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cstring-formatting-and-message-box-display"></a>Formatowanie obiektu CString i wyświetlanie okna komunikatu
Wiele funkcji służą do formatowania i przeanalizować `CString` obiektów. Zawsze do manipulowania można używać tych funkcji `CString` obiektów, ale są szczególnie użyteczne w przypadku formatowanie ciągów, które będą wyświetlane w oknie komunikatu tekstu.  
  
 Ta grupa funkcje także globalne procedury do wyświetlania okno komunikatu.  
  
### <a name="cstring-functions"></a>Cstring — funkcje  
  
|||  
|-|-|  
|[Afxextractsubstring —](#afxextractsubstring)|Wyodrębnia podciągów oddzielone jednego znaku w ciągu danego źródła.|  
|[Afxformatstring1 —](#afxformatstring1)|Substytuty ciągu znaków formatu "%1" w ciągu zawartych w tabeli ciągów.|  
|[Afxformatstring2 —](#afxformatstring2)|Substytuty dwa ciągi formatu znaków "%1" i "%2" w ciągu zawartych w tabeli ciągów.|  
|[AfxMessageBox](#afxmessagebox)|Wyświetla okno komunikatu.|  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="afxextractsubstring"></a>  Afxextractsubstring —  
 Ta funkcja globalna umożliwia wyodrębnianie podciągu z ciągu danego źródła.  
  
```   
BOOL AFXAPI AfxExtractSubString (
    CString& rString,  
    LPCTSTR lpszFullString,  
    int iSubString,  
    TCHAR chSep  = '\n'); 
```  
  
### <a name="parameters"></a>Parametry  
 *rString*  
 -   Odwołanie do [cstring —](../../atl-mfc-shared/using-cstring.md) obiekt, który otrzyma poszczególnych podciąg.  
  
 *lpszFullString*  
 -   Ciąg zawierający pełny tekst ciąg do wyodrębniania.  
  
 *iSubString*  
 -   Liczony od zera indeks podciąg do wyodrębniania *lpszFullString*.  
  
 *chSep*  
 -   Znak separatora używany do ograniczania podciągów.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli funkcja pomyślnie wyodrębnione substring w indeksie podana; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest przydatna dla wyodrębnianych wiele podciągów z ciągu źródła, jeśli znane pojedynczy znak oddziela każdego podciąg. Ta funkcja wyszukiwanie od początku `lpszFullString` parametru zawsze jest ona wywoływana.  
  
 Ta funkcja zwróci wartość FALSE, jeśli albo `lpszFullString` ma ustawioną wartość **NULL** lub funkcja dociera do końca `lpszFullString` nie `iSubString`wystąpienia + 1 znak separatora określony. `rString` Parametru nie zostaną zmodyfikowane od oryginalnej wartości, jeśli `lpszFullString` ustawiono **NULL**; w przeciwnym razie `rString` parametr jest ustawiony na pusty ciąg, jeśli nie można wyodrębnić podciąg dla określonego Indeks.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="afxformatstring1"></a>  Afxformatstring1 —  
 Zastępuje ciąg wskazywana przez `lpsz1` dla dowolnych wystąpień znaków "%1" w ciągu zasobu szablon wskazywanego przez `nIDS`.  
  
```  
void  AfxFormatString1(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1); 
```  
  
### <a name="parameters"></a>Parametry  
 `rString`  
 Odwołanie do `CString` obiekt, który będzie zawierać wynikowy ciąg po wykonaniu podstawienia.  
  
 `nIDS`  
 Identyfikator zasobu ciągu szablonu, na którym zostanie wykonane podstawienie.  
  
 `lpsz1`  
 Ciąg, który zastąpi format znaków "%1" w ciągu szablonu.  
  
### <a name="remarks"></a>Uwagi  
 Nowo utworzoną ciągu są przechowywane w `rString`. Na przykład, jeśli ciąg w tabeli ciągów jest "Plik %1 nie znaleziono" i `lpsz1` jest równa "C:\MYFILE. Pliki TXT", następnie `rString` będzie zawierać ciąg"plik C:\MYFILE. TXT nie znaleziono". Ta funkcja jest przydatna do formatowania ciągi wysyłane do komunikatów i innych oknach.  
  
 Jeśli format znaków "%1" ma więcej niż raz w ciągu, zostanie podjęta wielu podstawienia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="afxformatstring2"></a>  Afxformatstring2 —  
 Zastępuje ciąg wskazywana przez `lpsz1` dla dowolnych wystąpień znaków "%1", a ciąg wskazywana przez `lpsz2` dla dowolnych wystąpień znaków "%2" w ciągu zasobu szablon wskazywanego przez `nIDS`.  
  
```   
void AfxFormatString2(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1,  
    LPCTSTR lpsz2); 
```  
  
### <a name="parameters"></a>Parametry  
 `rString`  
 Odwołanie do `CString` który będzie zawierał wynikowy ciąg po wykonaniu podstawienia.  
  
 `nIDS`  
 Identyfikator tabeli ciąg ciąg szablonu, na którym zostanie wykonane podstawienie.  
  
 `lpsz1`  
 Ciąg, który zastąpi format znaków "%1" w ciągu szablonu.  
  
 `lpsz2`  
 Ciąg, który zastąpi format znaków "%2" w ciągu szablonu.  
  
### <a name="remarks"></a>Uwagi  
 Nowo utworzoną ciągu są przechowywane w `rString`. Na przykład, jeśli ciąg w tabeli ciągów jest "Plik %1 nie odnaleziono w katalogu %2" `lpsz1` wskazuje "MÓJ_PLIK. TXT"i `lpsz2` wskazuje"C:\MYDIR", następnie `rString` będzie zawierać ciąg"plik MÓJ_PLIK. Nie odnaleziono w katalogu C:\MYDIR TXT"  
  
 Jeśli format znaków "%1" lub "%2" występuje w ciągu więcej niż raz, nastąpi wielu podstawienia. Nie mają być w kolejności numerycznej.  
  
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
 `lpszText`  
 Wskazuje `CString` obiektu lub zerem ciągu zawierający komunikat, który ma być wyświetlany w oknie komunikatu.  
  
 `nType`  
 Style okna komunikatu. Zastosuj wszelkie z [Style okna komunikatu](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) do pola.  
  
 `nIDHelp`  
 Identyfikator kontekstu pomocy dla komunikatu; 0 wskazuje, że aplikacji domyślny kontekst pomocy będą używane.  
  
 `nIDPrompt`  
 Unikatowy identyfikator używany do ciągu w tablicy ciągów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli nie ma wystarczającej ilości pamięci do wyświetlenia w oknie komunikatu; w przeciwnym razie jest jedną z następujących wartości zwracane:  
  
- **IDABORT** przycisk Przerwij został wybrany.  
  
- **IDCANCEL** wybrano przycisku Anuluj.  
  
- **IDIGNORE** przycisk Ignoruj został wybrany.  
  
- **IDNO** wybrano przycisk nie.  
  
- **IDOK** wybrano przycisku OK.  
  
- **IDRETRY** wybrano przycisk Ponów próbę.  
  
- **IDYES** wybrano przycisku Tak.  
  
 Jeśli okno komunikatu znajduje się przycisk Anuluj, **IDCANCEL** wartość zostanie zwrócona w przypadku naciśnięciu klawisza ESC, albo przycisk Anuluj jest zaznaczony. Jeśli w oknie komunikatu nie przycisk Anuluj, naciskając klawisz ESC nie ma znaczenia.  
  
 Funkcje [afxformatstring1 —](#afxformatstring1) i [afxformatstring2 —](#afxformatstring2) mogą być przydatne podczas formatowania tekstu pojawiającego się w oknie komunikatu.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy formularz pojawia się przeciążona funkcja wyświetla ciąg tekstowy wskazywana przez `lpszText` w oknie komunikatu i używa `nIDHelp` do opisywania kontekstu pomocy. Aby przejść do skojarzonego tematu pomocy, gdy użytkownik naciśnie klawisz Pomocy (zazwyczaj F1) używany jest kontekst pomocy.  
  
 Drugi formularz funkcji używa zasobu ciągu z Identyfikatorem `nIDPrompt` Aby wyświetlić komunikat w oknie komunikatu. Strona pomocy skojarzone znajduje się za pomocą wartości `nIDHelp`. Jeśli wartość domyślną `nIDHelp` jest używana (-1), identyfikator zasobu ciągu, `nIDPrompt`, jest używany dla kontekstu pomocy. Aby uzyskać więcej informacji na temat definiowania kontekstów pomocy, zobacz [28 Uwaga techniczna](../../mfc/tn028-context-sensitive-help-support.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)   
 [CStringT, klasa](../../atl-mfc-shared/reference/cstringt-class.md)
