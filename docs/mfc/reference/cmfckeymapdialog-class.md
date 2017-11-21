---
title: Klasa CMFCKeyMapDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
dev_langs: C++
helpviewer_keywords:
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 27278d64ab1aef17149a3b4c166cff9c302e29ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfckeymapdialog-class"></a>Klasa CMFCKeyMapDialog
`CMFCKeyMapDialog` Klasa obsługuje formant, który mapuje poleceń z klawiszami na klawiaturze.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCKeyMapDialog : public CDialogEx  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|Konstruuje `CMFCKeyMapDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCKeyMapDialog::DoModal](#domodal)|Wyświetla okno dialogowe mapowania klawiatury.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Wywoływane przez platformę, by kompilacji ciąg opisujący klucza mapowania. Domyślnie ten ciąg zawiera nazwę polecenia, klawiszy skrótów i opis klawiszy skrótów.|  
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Pobiera ciąg, który zawiera listę klawiszy skrótu skojarzony z określonego polecenia.|  
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Wywoływane przez platformę przed wstawieniem nowy element do formantu listy wewnętrzny, który obsługuje kontrolkę mapowania klawiatury.|  
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Wywoływane przez platformę, by wydrukować nagłówka mapy klawiatury na nowej stronie.|  
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Wywoływane przez platformę, by wydrukować element mapowania klawiatury.|  
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Wywoływane przez platformę, by ustawić podpisy kolumn w formancie listy wewnętrznej, który obsługuje kontrolkę mapowania klawiatury.|  
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Wywoływane przez platformę, gdy użytkownik kliknie **drukowania** przycisku.|  
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Wywoływane przez platformę, by ustawić szerokość kolumn w formancie listy wewnętrznej, który obsługuje kontrolkę mapowania klawiatury.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `CMFCKeyMapDialog` klasy do zaimplementowania okno dialogowe mapowania klawiatury o zmiennym rozmiarze. Okno dialogowe używa formantu widoku listy, aby wyświetlić skróty klawiaturowe i skojarzone z nimi polecenia.  
  
 Aby użyć `CMFCKeyMapDialog` klasy w aplikacji, Przekaż wskaźnik do głównego okna ramowego jako parametr `CMFCKeyMapDialog` konstruktora. Następnie wywołaj `DoModal` metodę, aby uruchomić modalne okno dialogowe.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxkeymapdialog.h  
  
##  <a name="cmfckeymapdialog"></a>CMFCKeyMapDialog::CMFCKeyMapDialog  
 Konstruuje `CMFCKeyMapDialog` obiektu.  
  
```  
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bEnablePrint=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWndParentFrame`  
 Wskaźnik do okna nadrzędnego `CMFCKeyMapDialog` obiektu.  
  
 [in]`bEnablePrint`  
 `TRUE`Jeśli można go wydrukować lista klawiszy skrótów; w przeciwnym razie `FALSE`. Wartość domyślna to `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCKeyMapDialog` klasy. Ten przykład jest częścią [programu Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]  
  
##  <a name="domodal"></a>CMFCKeyMapDialog::DoModal  
 Wyświetla okno dialogowe mapowania klawiatury.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Całkowita, takich jak `IDOK` lub `IDCANCEL`, która jest przekazywany do [CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog) metody. Metoda z kolei zamknięcie okna dialogowego. Aby uzyskać więcej informacji, zobacz [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).  
  
### <a name="remarks"></a>Uwagi  
 Okno dialogowe mapowania klawiatury umożliwia wybieranie i przypisywanie klawiszy skrótów do różnych kategorii poleceń. Ponadto klucze wybrany Akcelerator i ich opisy można skopiować do Schowka.  
  
##  <a name="formatitem"></a>CMFCKeyMapDialog::FormatItem  
 Wywoływane przez platformę, by kompilacji ciąg opisujący klucza mapowania. Domyślnie ten ciąg zawiera nazwę polecenia, klawiszy skrótów i opis klawiszy skrótów.  
  
```  
virtual CString FormatItem(int nItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nItem`  
 Liczony od zera indeks elementu na wewnętrznej liście mapowań klucza.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` obiekt, który zawiera tekst sformatowany elementu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcommandkeys"></a>CMFCKeyMapDialog::GetCommandKeys  
 Pobiera wartość ciągu. Ciąg zawiera listę klawiszy skrótów, które są skojarzone z określonego polecenia.  
  
```  
virtual CString GetCommandKeys(UINT uiCmdID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmdID`  
 Identyfikator polecenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozdzielana średnikami (';') lista klawiszy skrótu skojarzony z określonego polecenia.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="oninsertitem"></a>CMFCKeyMapDialog::OnInsertItem  
 Wywoływane przez platformę, zanim nowy element jest wstawiany formant listy wewnętrznej, który obsługuje sterowania mapowania klawiatury.  
  
```  
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,  
    int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pButton`  
 Wskaźnik do przycisku paska narzędzi, który jest używany do mapowania klawiatury kombinacji klawiszy polecenia nazwę i opis. Element mapy klucza jest przechowywany w formancie listy wewnętrznej.  
  
 [in]`nItem`  
 Liczony od zera indeks, który określa, gdzie Wstaw nowy element mapy klucza w formancie listy wewnętrznej.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onprintheader"></a>CMFCKeyMapDialog::OnPrintHeader  
 Wywoływane przez platformę, by wydrukować nagłówka mapy klawiatury na nowej stronie.  
  
```  
virtual int OnPrintHeader(
    CDC& dc,  
    int nPage,  
    int cx) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dc`  
 Kontekst urządzenia dla drukarki.  
  
 [in]`nPage`  
 Numer strony do drukowania.  
  
 [in]`cx`  
 Przesunięcie w poziomie nagłówka, w pikselach.  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia wysokość drukowanej tekstu. Aby uzyskać więcej informacji, zobacz sekcję zwrócić wartość [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext).  
  
### <a name="remarks"></a>Uwagi  
 Platformę używa tej metody do drukowania mapy klawiatury. Domyślnie ta metoda Wyświetla numer strony, nazwa aplikacji i tytuł okna dialogowego.  
  
##  <a name="onprintitem"></a>CMFCKeyMapDialog::OnPrintItem  
 Wywoływane przez platformę, by wydrukować element mapowania klawiatury.  
  
```  
virtual int OnPrintItem(
    CDC& dc,  
    int nItem,  
    int y,  
    int cx,  
    BOOL bCalcHeight) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dc`  
 Kontekst urządzenia drukarki.  
  
 [in]`nItem`  
 Liczony od zera indeks elementu do drukowania.  
  
 [in]`y`  
 Przesunięcie w pionie między górnej części strony i pozycja elementu.  
  
 [in]`cx`  
 Przesunięcie w poziomie między po lewej stronie i pozycja elementu.  
  
 [in]`bCalcHeight`  
 `TRUE`Aby obliczyć najlepsze wysokość elementu wydruku; `FALSE` obcięcia wydruku elementu, tak aby zmieścił domyślna przestrzeń.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wysokość elementu wydruku.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę, aby wydrukować elementu okna dialogowego kluczy mapy. Domyślnie ta metoda Wyświetla nazwa polecenia, klawiszy skrótów i opis polecenia do elementu.  
  
##  <a name="onsetcolumns"></a>CMFCKeyMapDialog::OnSetColumns  
 Wywoływane przez platformę, by ustawić podpisy kolumn w formancie listy wewnętrznej, który obsługuje kontrolkę mapowania klawiatury.  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda uzyskuje podpisy kolumn z trzech zasobów. Polecenie Podpis kolumny pochodzi z IDS_AFXBARRES_COMMAND, podpis kolumny klucza jest z IDS_AFXBARRES_KEYS, a podpis opis kolumny jest IDS_AFXBARRES_DESCRIPTION.  
  
##  <a name="printkeymap"></a>CMFCKeyMapDialog::PrintKeyMap  
 Wywoływane przez platformę, gdy użytkownik kliknie **drukowania** przycisku.  
  
```  
virtual void PrintKeyMap();
```  
  
### <a name="remarks"></a>Uwagi  
 `PrintKeyMap` Metoda drukuje kluczy mapy. Inicjuje nowe zadanie drukowania, a następnie w wielokrotnie wywołuje [CMFCKeyMapDialog::OnPrintHeader](#onprintheader) i [CMFCKeyMapDialog::OnPrintItem](#onprintitem) metody do momentu są drukowane mapowań klucza.  
  
##  <a name="setcolumnswidth"></a>CMFCKeyMapDialog::SetColumnsWidth  
 Wywoływane przez platformę, by ustawić szerokość kolumn w formancie listy wewnętrznej, który obsługuje kontrolkę mapowania klawiatury.  
  
```  
virtual void SetColumnsWidth();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia wewnętrzny listy kolumn formantu do domyślnej szerokości. Po pierwsze jest obliczana szerokość kolumny klawiszy skrótów. Następnie jedna trzecia szerokości jest przydzielony do kolumny polecenia i pozostałych dwóch jest przydzielony do kolumny opis.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)
