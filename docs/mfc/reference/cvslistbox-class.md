---
title: Klasa CVSListBox | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
dev_langs:
- C++
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 946c82d4f558974d548a40af0b14e63f7ccebf4e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680583"
---
# <a name="cvslistbox-class"></a>Klasa CVSListBox
`CVSListBox` Klasa obsługuje formant edytowalnej listy.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CVSListBox : public CVSListBoxBase  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CVSListBox::CVSListBox](#cvslistbox)|Konstruuje `CVSListBox` obiektu.|  
|`CVSListBox::~CVSListBox`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CVSListBox::AddItem](#additem)|Dodaje ciąg do kontrolki listy. (Przesłania `CVSListBoxBase::AddItem`.)|  
|[CVSListBox::EditItem](#edititem)|Rozpoczyna operację edycji tekstu element formantu listy. (Przesłania `CVSListBoxBase::EditItem`.)|  
|[CVSListBox::GetCount](#getcount)|Pobiera liczbę ciągów w formant edytowalnej listy. (Przesłania `CVSListBoxBase::GetCount`.)|  
|[CVSListBox::GetItemData](#getitemdata)|Pobiera wartość 32-bitowych specyficzne dla aplikacji, który jest skojarzony z elementem formant edytowalnej listy. (Przesłania `CVSListBoxBase::GetItemData`.)|  
|[CVSListBox::GetItemText](#getitemtext)|Pobiera tekst elementu formant edytowalnej listy. (Przesłania `CVSListBoxBase::GetItemText`.)|  
|[CVSListBox::GetSelItem](#getselitem)|Pobiera liczony od zera Indeks aktualnie wybranego elementu w formant edytowalnej listy. (Przesłania `CVSListBoxBase::GetSelItem`.)|  
|`CVSListBox::PreTranslateMessage`|Wykonuje translację komunikatów okien, zanim zostaną rozesłane do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkcje Windows. Aby uzyskać więcej informacji i składnia metody, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Przesłania `CVSListBoxBase::PreTranslateMessage`.)|  
|[CVSListBox::RemoveItem](#removeitem)|Usuwa element z formant edytowalnej listy. (Przesłania `CVSListBoxBase::RemoveItem`.)|  
|[CVSListBox::SelectItem](#selectitem)|Wybiera ciągiem formant edytowalnej listy. (Przesłania `CVSListBoxBase::SelectItem`.)|  
|[CVSListBox::SetItemData](#setitemdata)|Kojarzy specyficzne dla aplikacji 32-bitową wartość za pomocą elementu formant edytowalnej listy. (Przesłania `CVSListBoxBase::SetItemData`.)|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CVSListBox::GetListHwnd](#getlisthwnd)|Zwraca uchwyt do bieżącego osadzone kontrolka widoku listy.|  
  
## <a name="remarks"></a>Uwagi  
 `CVSListBox` Klasa udostępnia zestaw przycisków edycji, który umożliwia użytkownikowi tworzenie, modyfikowanie, usuwać ani zmieniać kolejności elementów w formancie listy.  
  
 Poniżej znajduje się obraz formant edytowalnej listy. Wpis listy druga jest zatytułowana "Item2 —", został wybrany do edycji.  
  
 ![Kontrolka CVSListBox](../../mfc/reference/media/cvslistbox.png "cvslistbox")  
  
 Jeśli używasz Edytor zasobów, aby dodać formant edytowalnej listy, zwróć uwagę, że **przybornika** okienka edytora nie dostarczył kontrolki wstępnie zdefiniowanej listy można edytować. Zamiast tego Dodaj formant statyczny, takie jak **pole grupy** kontroli. Struktura używa kontrolki statycznej jako symbolu zastępczego do określenia rozmiaru i położenia formant edytowalnej listy.  
  
 Aby użyć formant edytowalnej listy w szablonu okna dialogowego, należy zadeklarować `CVSListBox` zmiennej w klasie okno dialogowe. Aby umożliwić wymianę danych między zmienną i kontrolki, należy zdefiniować `DDX_Control` wpis — makro `DoDataExchange` metoda okna dialogowego. Domyślnie formant edytowalnej listy jest tworzone bez przyciski edytowania. Umożliwiają dziedziczonej metody CVSListBoxBase::SetStandardButtons przyciski edytowania.  
  
 Aby uzyskać więcej informacji, zobacz katalog przykładów `New Controls` przykładowe pliki Page3.cpp i Page3.h.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CStatic](../../mfc/reference/cstatic-class.md)  
  
 `CVSListBoxBase`  
  
 [CVSListBox](../../mfc/reference/cvslistbox-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxvslistbox.h  
  
##  <a name="additem"></a>  CVSListBox::AddItem  
 Dodaje ciąg do kontrolki listy.  
  
```  
virtual int AddItem(
    const CString& strIext,  
    DWORD_PTR dwData=0,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *strIext*  
 Odwołanie do ciągu.  
  
 [in] *dwData*  
 Specyficzne dla aplikacji 32-bitową wartość skojarzoną z ciągiem. Wartość domyślna to 0.  
  
 [in] *iIndex*  
 Liczony od zera indeks położenie, w którym będą przechowywane w ciągu. Jeśli *iIndex* parametr ma wartość -1, ciąg zostanie dodany na końcu listy. Wartość domyślna to -1.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks pozycji w ciągu w kontrolce listy.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CVSListBox::GetItemData](#getitemdata) metodę, aby pobrać wartość, która jest określona przez *dwData* parametru. Ta wartość może być liczbą całkowitą określonych aplikacji lub wskaźnik do innych danych.  
  
##  <a name="cvslistbox"></a>  CVSListBox::CVSListBox  
 Konstruuje `CVSListBox` obiektu.  
  
```  
CVSListBox();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="edititem"></a>  CVSListBox::EditItem  
 Rozpoczyna operację edycji tekstu element formantu listy.  
  
```  
virtual BOOL EditItem(int iIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Liczony od zera indeks elementu kontrolki listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli operacja edytowania uruchamia się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Użytkownik uruchamia operację edycji, klikając etykietę elementu lub naciskając **F2** lub **spacja** klucza, gdy element ma fokus.  
  
##  <a name="getcount"></a>  CVSListBox::GetCount  
 Pobiera liczbę ciągów w formant edytowalnej listy.  
  
```  
virtual int GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w formancie listy.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że liczba jest większa o jeden od ostatniego elementu wartość indeksu, ponieważ ten indeks jest liczony od zera.  
  
##  <a name="getitemdata"></a>  CVSListBox::GetItemData  
 Pobiera wartość 32-bitowych specyficzne dla aplikacji, który jest skojarzony z elementem formant edytowalnej listy.  
  
```  
virtual DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Liczony od zera indeks elementu formant edytowalnej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 32-bitową wartość, który jest skojarzony z określonym elementem.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CVSListBox::SetItemData](#setitemdata) lub [CVSListBox::AddItem](#additem) metodę, aby skojarzyć 32-bitową wartość z listy element kontroli. Ta wartość może być liczbą całkowitą określonych aplikacji lub wskaźnik do innych danych.  
  
##  <a name="getitemtext"></a>  CVSListBox::GetItemText  
 Pobiera tekst elementu formant edytowalnej listy.  
  
```  
virtual CString GetItemText(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iIndex`  
 Liczony od zera indeks elementu formant edytowalnej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt, który zawiera tekst określony element.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getlisthwnd"></a>  CVSListBox::GetListHwnd  
 Zwraca uchwyt do bieżącego osadzone kontrolka widoku listy.  
  
```  
virtual HWND GetListHwnd() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do formantu widoku listy osadzonych.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda służy do pobierania dojścia do kontrolka widoku listy osadzonych, która obsługuje `CVSListBox` klasy.  
  
##  <a name="getselitem"></a>  CVSListBox::GetSelItem  
 Pobiera liczony od zera Indeks aktualnie wybranego elementu w formant edytowalnej listy.  
  
```  
virtual int GetSelItem() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli ta metoda zakończy się pomyślnie, liczony od zera Indeks aktualnie wybranego elementu; w przeciwnym razie, wartość -1.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="removeitem"></a>  CVSListBox::RemoveItem  
 Usuwa element z formant edytowalnej listy.  
  
```  
virtual BOOL RemoveItem(int iIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Liczony od zera indeks elementu formant edytowalnej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli określony element został usunięty; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="selectitem"></a>  CVSListBox::SelectItem  
 Wybiera ciągiem formant edytowalnej listy.  
  
```  
virtual BOOL SelectItem(int iItem);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *towaru*  
 Liczony od zera indeks elementu formant edytowalnej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wybiera określony element, a jeśli jest to konieczne, przewinąć element w celu wyświetlenia.  
  
##  <a name="setitemdata"></a>  CVSListBox::SetItemData  
 Kojarzy specyficzne dla aplikacji 32-bitową wartość za pomocą elementu formant edytowalnej listy.  
  
```  
virtual void SetItemData(
    int iIndex,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Liczony od zera indeks elementu formant edytowalnej listy.  
  
 [in] *dwData*  
 32-bitową wartość. Ta wartość może być liczbą całkowitą określonych aplikacji lub wskaźnik do innych danych.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
