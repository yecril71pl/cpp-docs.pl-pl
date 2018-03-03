---
title: Klasa CD2DTextLayout | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
dev_langs:
- C++
helpviewer_keywords:
- CD2DTextLayout [MFC], CD2DTextLayout
- CD2DTextLayout [MFC], Create
- CD2DTextLayout [MFC], Destroy
- CD2DTextLayout [MFC], Get
- CD2DTextLayout [MFC], GetFontFamilyName
- CD2DTextLayout [MFC], GetLocaleName
- CD2DTextLayout [MFC], IsValid
- CD2DTextLayout [MFC], ReCreate
- CD2DTextLayout [MFC], SetFontFamilyName
- CD2DTextLayout [MFC], SetLocaleName
- CD2DTextLayout [MFC], m_pTextLayout
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9dc216014fb88ac7995b9283ab59d0c011f3184f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dtextlayout-class"></a>Klasa CD2DTextLayout
Otoka dla IDWriteTextLayout.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DTextLayout : public CD2DResource;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|Tworzy obiekt CD2DTextLayout.|  
|[CD2DTextLayout:: ~ CD2DTextLayout](#cd2dtextlayout__~cd2dtextlayout)|Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D układu tekstu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DTextLayout::Create](#create)|Tworzy CD2DTextLayout. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DTextLayout::Destroy](#destroy)|Niszczy obiektu CD2DTextLayout. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DTextLayout::Get](#get)|Zwraca interfejs IDWriteTextLayout|  
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|Kopiuje nazwę rodziny czcionek tekstu w określonej pozycji.|  
|[CD2DTextLayout::GetLocaleName](#getlocalename)|Pobiera nazwę ustawień regionalnych tekstu w określonej pozycji.|  
|[CD2DTextLayout::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DTextLayout::ReCreate](#recreate)|Ponownie tworzy CD2DTextLayout. (Przesłania [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|  
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|Nazwy rodziny czcionek zerem zestawów dla tekstu w zakresie określony tekst.|  
|[CD2DTextLayout::SetLocaleName](#setlocalename)|Ustawia nazwę ustawień regionalnych dla tekstu w zakresie określony tekst.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DTextLayout::operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|Zwraca interfejs IDWriteTextLayout|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|Wskaźnik do IDWriteTextLayout.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="_dtorcd2dtextlayout"></a>CD2DTextLayout:: ~ CD2DTextLayout  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D układu tekstu.  
  
```  
virtual ~CD2DTextLayout();
```  
  
##  <a name="cd2dtextlayout"></a>CD2DTextLayout::CD2DTextLayout  
 Tworzy obiekt CD2DTextLayout.  
  
```  
CD2DTextLayout(
    CRenderTarget* pParentTarget,  
    const CString& strText,  
    CD2DTextFormat& textFormat,  
    const CD2DSizeF& sizeMax,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
 `strText`  
 Cstring — obiekt, który zawiera ciąg do utworzenia nowego obiektu CD2DTextLayout z.  
  
 `textFormat`  
 Cstring — obiekt, który zawiera format do zastosowania do ciągu.  
  
 `sizeMax`  
 Rozmiar pola układu.  
  
 `bAutoDestroy`  
 Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).  
  
##  <a name="create"></a>CD2DTextLayout::Create  
 Tworzy CD2DTextLayout.  
  
```  
virtual HRESULT Create(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="destroy"></a>CD2DTextLayout::Destroy  
 Niszczy obiektu CD2DTextLayout.  
  
```  
virtual void Destroy();
```  
  
##  <a name="get"></a>CD2DTextLayout::Get  
 Zwraca interfejs IDWriteTextLayout  
  
```  
IDWriteTextLayout* Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu IDWriteTextLayout lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="getfontfamilyname"></a>CD2DTextLayout::GetFontFamilyName  
 Kopiuje nazwę rodziny czcionek tekstu w określonej pozycji.  
  
```  
CString GetFontFamilyName(
    UINT32 currentPosition,  
    DWRITE_TEXT_RANGE* textRange = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `currentPosition`  
 Pozycja tekstu do sprawdzenia.  
  
 `textRange`  
 Zakres tekstu, który ma taką samą formatowanie jako tekst w określonym przez currentPosition pozycji. Oznacza to, że ma dokładne formatowanie jako pozycja określona, w tym między innymi nazwę rodziny czcionek.  
  
### <a name="return-value"></a>Wartość zwracana  
 Cstring — obiekt, który zawiera nazwę bieżącego rodziny czcionek.  
  
##  <a name="getlocalename"></a>CD2DTextLayout::GetLocaleName  
 Pobiera nazwę ustawień regionalnych tekstu w określonej pozycji.  
  
```  
CString GetLocaleName(
    UINT32 currentPosition,  
    DWRITE_TEXT_RANGE* textRange = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `currentPosition`  
 Pozycja tekstu do sprawdzenia.  
  
 `textRange`  
 Zakres tekstu, który ma taką samą formatowanie jako tekst w określonym przez currentPosition pozycji. Oznacza to, że ma dokładne formatowanie jako pozycja określona, w tym między innymi Nazwa ustawień regionalnych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Cstring — obiekt, który zawiera bieżąca nazwa ustawień regionalnych.  
  
##  <a name="isvalid"></a>CD2DTextLayout::IsValid  
 Sprawdzanie poprawności zasobów  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zasób jest nieprawidłowy; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_ptextlayout"></a>CD2DTextLayout::m_pTextLayout  
 Wskaźnik do IDWriteTextLayout.  
  
```  
IDWriteTextLayout* m_pTextLayout;  
```  
  
##  <a name="operator_idwritetextlayout_star"></a>CD2DTextLayout::operator IDWriteTextLayout *  
 Zwraca interfejs IDWriteTextLayout  
  
```  
operator IDWriteTextLayout*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu IDWriteTextLayout lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="recreate"></a>CD2DTextLayout::ReCreate  
 Ponownie tworzy CD2DTextLayout.  
  
```  
virtual HRESULT ReCreate(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="setfontfamilyname"></a>CD2DTextLayout::SetFontFamilyName  
 Nazwy rodziny czcionek zerem zestawów dla tekstu w zakresie określony tekst.  
  
```  
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,  
    DWRITE_TEXT_RANGE textRange);
```  
  
### <a name="parameters"></a>Parametry  
 `pwzFontFamilyName`  
 Nazwę rodziny czcionek, która ma zastosowanie do ciągu cały tekst w zakresie określonym przez textRange  
  
 `textRange`  
 Zakres tekstu, którego dotyczy ta zmiana  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE  
  
##  <a name="setlocalename"></a>CD2DTextLayout::SetLocaleName  
 Ustawia nazwę ustawień regionalnych dla tekstu w zakresie określony tekst.  
  
```  
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,  
    DWRITE_TEXT_RANGE textRange);
```  
  
### <a name="parameters"></a>Parametry  
 `pwzLocaleName`  
 Ciąg nazwy zerem ustawień regionalnych  
  
 `textRange`  
 Zakres tekstu, którego dotyczy ta zmiana  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
