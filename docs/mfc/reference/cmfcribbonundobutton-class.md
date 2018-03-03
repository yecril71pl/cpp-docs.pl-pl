---
title: Klasa CMFCRibbonUndoButton | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 720a1de11dcf4c37b4b321bb0e014a9ae4e2e459
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonundobutton-class"></a>Klasa CMFCRibbonUndoButton
`CMFCRibbonUndoButton` Klasa implementuje przycisk listy rozwijanej, który zawiera najnowsze poleceń użytkownika. Użytkownicy mogą wybrać co najmniej jeden z najnowszych poleceń, z listy rozwijanej, aby cofnąć je albo wykonaj ponownie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonUndoButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Tworzy nową `CMFCRibbonUndoButton` obiektu przy użyciu Identyfikatora polecenia, który określisz, tekst etykiety i obrazów z listy obrazów obiektu nadrzędnego.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Dodaje nową akcję do listy akcji.|  
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Czyści listę akcji, czyli z listy rozwijanej.|  
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Określa liczbę elementów, które użytkownik wybrał z listy rozwijanej.|  
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Wskazuje, czy obiekt zawiera menu.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCRibbonUndoButton` Klasy używa stosu do reprezentowania listy rozwijanej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCRibbonUndoButton` klasy, a następnie dodaj nową akcję do listy akcji. Następujący fragment kodu jest częścią [próbki gadżetów wstążki](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxribbonundobutton.h  
  
##  <a name="addundoaction"></a>CMFCRibbonUndoButton::AddUndoAction  
 Dodaje nową akcję do listy akcji.  
  
```  
void AddUndoAction(LPCTSTR lpszLabel);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszLabel`  
 Etykieta akcji, który będzie wyświetlany na liście rozwijanej.  
  
##  <a name="cleanupundolist"></a>CMFCRibbonUndoButton::CleanUpUndoList  
 Czyści listę akcji, czyli z listy rozwijanej.  
  
```  
void CleanUpUndoList();
```  
  
##  <a name="cmfcribbonundobutton"></a>CMFCRibbonUndoButton::CMFCRibbonUndoButton  
 Tworzy nową `CMFCRibbonUndoButton` obiektu przy użyciu Identyfikatora polecenia, który określisz, tekst etykiety i obrazów z listy obrazów obiektu nadrzędnego.  
  
```  
CMFCRibbonUndoButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex=-1,  
    int nLargeImageIndex=-1);

 
CMFCRibbonUndoButton(
    UINT nID,  
    LPCTSTR lpszText,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nID`  
 Określa identyfikator polecenia.  
  
 [in]`lpszText`  
 Określa tekst etykiety przycisku.  
  
 [in]`nSmallImageIndex`  
 Liczony od zera indeks obiektu nadrzędnego dla przycisku mały obraz na liście obrazów.  
  
 [in]`nLargeImageIndex`  
 Liczony od zera indeks obrazu na liście obiektu nadrzędnego dla dużych obrazu przycisku.  
  
 [in]`hIcon`  
 Dojście do ikonę, która służy jako obrazu przycisku.  
  
##  <a name="getactionnumber"></a>CMFCRibbonUndoButton::GetActionNumber  
 Określa liczbę elementów, które użytkownik wybrał z listy rozwijanej.  
  
```  
int GetActionNumber() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów, które wybrane przez użytkownika.  
  
##  <a name="hasmenu"></a>CMFCRibbonUndoButton::HasMenu  
 Wskazuje, czy obiekt zawiera menu.  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)   
 [Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
