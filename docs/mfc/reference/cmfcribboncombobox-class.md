---
title: Klasa CMFCRibbonComboBox | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5894f1fc9bd901bef6e830250f4e1f8e9bdd335
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040757"
---
# <a name="cmfcribboncombobox-class"></a>Klasa CMFCRibbonComboBox
`CMFCRibbonComboBox` Klasa implementuje kontrolki pola kombi dodawanego do pasek wstążki, panel Wstążki lub menu podręcznego wstążki.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonComboBox : public CMFCRibbonEdit  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="constructors"></a>Konstruktorów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|Tworzy obiekt CMFCRibbonComboBox.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonComboBox::AddItem](#additem)|Dołącza unikatowy element do listy.|  
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|Usuwa określony element z listy.|  
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Określa, czy pole listy można zmienić rozmiar, gdy jego rozwijać.|  
|[CMFCRibbonComboBox::FindItem](#finditem)|Zwraca indeks pierwszego elementu w polu listy pasującej określonego ciągu.|  
|[CMFCRibbonComboBox::GetCount](#getcount)|Zwraca liczbę elementów w polu listy.|  
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Pobiera indeks aktualnie zaznaczonego elementu w polu listy.|  
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Pobiera wysokość pola listy, gdy pole listy jest rozwijana.|  
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|Zwraca rozmiar pola kombi wyświetlany w trybie pośrednich.|  
|[CMFCRibbonComboBox::GetItem](#getitem)|Zwraca ciąg skojarzony z elementem od określonego indeksu w polu listy.|  
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Zwraca dane skojarzone z elementem od określonego indeksu w polu listy.|  
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Wskazuje, czy formant zawiera pole edycji.|  
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Wskazuje, czy pole listy można zmieniać.|  
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Wywoływane przez platformę, gdy użytkownik wybierze element w polu listy.|  
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|Usuwa wszystkie elementy w polu listy i czyści pole edycji.|  
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Wybiera element w polu listy.|  
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Ustawia wysokość pola listy, gdy jest rozwijana.|  
  
## <a name="remarks"></a>Uwagi  
 Pole kombi wstążki składa się z pola listy, w połączeniu z statyczną etykietę lub etykietę, którą można edytowane przez użytkownika. Należy określić typ ma podczas tworzenia Twojej pola kombi wstążki.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCRibbonComboBox` klasy, Dodaj element do pola kombi, wybierz element w polu kombi i dodać pole kombi na panelu.  
  
 [!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxribboncombobox.h  
  
##  <a name="additem"></a>  CMFCRibbonComboBox::AddItem  
 Dołącza unikatowy element do listy.  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszItem*  
 Ciąg element do dodania.  
  
 [in] *dwData*  
 Dane skojarzone z elementem do dodania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks elementu dołączany.  
  
##  <a name="cmfcribboncombobox"></a>  CMFCRibbonComboBox::CMFCRibbonComboBox  
 Konstruuje `CMFCRibbonComboBox` obiektu.  
  
```  
public:  
CMFCRibbonComboBox(
    UINT nID,  
    BOOL bHasEditBox=TRUE,  
    Int nWidth=-1,  
    LPCTSTR lpszLabel=NULL,  
    Int nImage=-1);

protected:  
CMFCRibbonComboBox();
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nID*  
 Identyfikator pola kombi.  
  
 [in] *bHasEditBox*  
 `TRUE` Jeśli chcesz, aby pole edycji w formancie; `FALSE` inaczej.  
  
 [in] *nWidth*  
 Szerokość pola kombi w pikselach; lub wartość -1 domyślnej szerokości.  
  
 [in] *lpszLabel*  
 Wyświetl etykietę pola kombi.  
  
 [in] *nImage*  
 Indeks mały obraz pola kombi.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna szerokość to 108 pikseli.  
  
##  <a name="deleteitem"></a>  CMFCRibbonComboBox::DeleteItem  
 Usuwa określony element z listy.  
  
```  
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Liczony od zera indeks elementu do usunięcia.  
  
 [in] *dwData*  
 Dane skojarzone z elementem, który ma zostać usunięty.  
  
 [in] *lpszText*  
 Ciąg elementu do usunięcia. Jeśli istnieje wiele elementów z tych samych parametrach, pierwszy element zostanie usunięty.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli określony element został usunięty; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enabledropdownlistresize"></a>  CMFCRibbonComboBox::EnableDropDownListResize  
 Określa, czy pole listy można zmienić rozmiar, gdy jego rozwijać.  
  
```  
void EnableDropDownListResize(BOOL bEnable=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bWłączenie*  
 `TRUE` Aby umożliwić zmianę rozmiaru; `FALSE` można wyłączyć zmiany rozmiaru.  
  
### <a name="remarks"></a>Uwagi  
 Po włączeniu zmiana rozmiaru pola listy zmieni rozmiar, aby dopasować elementy, które są wyświetlane.  
  
##  <a name="finditem"></a>  CMFCRibbonComboBox::FindItem  
 Zwraca indeks pierwszego elementu w polu listy pasującej określonego ciągu.  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszText*  
 Ciąg elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks elementu; lub -1, jeśli element nie został znaleziony.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcount"></a>  CMFCRibbonComboBox::GetCount  
 Zwraca liczbę elementów w polu listy.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w polu listy lub 0, jeśli pole listy nie zawiera elementów.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcursel"></a>  CMFCRibbonComboBox::GetCurSel  
 Pobiera indeks aktualnie zaznaczonego elementu w polu listy.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera Indeks aktualnie zaznaczonego elementu w polu listy; lub -1, jeśli nie wybrano elementu.  
  
##  <a name="getdropdownheight"></a>  CMFCRibbonComboBox::GetDropDownHeight  
 Pobiera wysokość pola listy, gdy pole listy jest rozwijana.  
  
```  
int GetDropDownHeight();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wysokość w pikselach pola listy.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getintermediatesize"></a>  CMFCRibbonComboBox::GetIntermediateSize  
 Zwraca rozmiar pola kombi wyświetlany w trybie pośrednich.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar pola kombi.  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar zwrócił zależy od rozmiaru pola kombi wyświetlanych małe obrazy.  
  
##  <a name="getitem"></a>  CMFCRibbonComboBox::GetItem  
 Zwraca ciąg skojarzony z elementem od określonego indeksu w polu listy.  
  
```  
LPCTSTR GetItem(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik na ciąg, który jest skojarzony z elementem; w przeciwnym razie `NULL` , czy parametr indeks jest nieprawidłowy parametr indeksu wynosi -1, jeśli nie ma żadnego elementu zaznaczonego w polu kombi.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getitemdata"></a>  CMFCRibbonComboBox::GetItemData  
 Zwraca dane skojarzone z elementem od określonego indeksu w polu listy.  
  
```  
DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane skojarzone z elementem; lub równa 0, jeśli element nie istnieje lub parametr indeksu wynosi -1 i nie ma zaznaczonego elementu w polu listy.  
  
##  <a name="haseditbox"></a>  CMFCRibbonComboBox::HasEditBox  
 Wskazuje, czy formant zawiera pole edycji.  
  
```  
BOOL HasEditBox() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli formant zawiera pole edycji; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isresizedropdownlist"></a>  CMFCRibbonComboBox::IsResizeDropDownList  
 Wskazuje, czy pole listy można zmieniać.  
  
```  
BOOL IsResizeDropDownList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli można zmieniać w polu listy; w przeciwnym razie `FALSE`. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)  
  
### <a name="remarks"></a>Uwagi  
 Można włączyć pole Zmiana rozmiaru przy użyciu listy [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize) metody.  
  
##  <a name="onselectitem"></a>  CMFCRibbonComboBox::OnSelectItem  
 Wywoływane przez platformę, gdy użytkownik wybierze element w polu listy.  
  
```  
virtual void OnSelectItem(int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nItem*  
 Indeks wybranego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę metodę, aby przetworzyć wybór wejściowych użytkownika.  
  
##  <a name="removeallitems"></a>  CMFCRibbonComboBox::RemoveAllItems  
 Usuwa wszystkie elementy w polu listy i czyści pole edycji.  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="selectitem"></a>  CMFCRibbonComboBox::SelectItem  
 Wybiera element w polu listy.  
  
```  
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Liczony od zera indeks elementu w polu listy.  
  
 [in] *dwData*  
 Dane skojarzone z elementu w polu listy.  
  
 [in] *lpszText*  
 Ciąg elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setdropdownheight"></a>  CMFCRibbonComboBox::SetDropDownHeight  
 Ustawia wysokość pola listy, gdy jest rozwijana.  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nHeight*  
 Wysokość w pikselach pola listy.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna wysokość jest 150 pikseli.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)
