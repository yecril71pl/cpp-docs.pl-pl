---
title: Klasa CD2DTextFormat | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::Create
- AFXRENDERTARGET/CD2DTextFormat::Destroy
- AFXRENDERTARGET/CD2DTextFormat::Get
- AFXRENDERTARGET/CD2DTextFormat::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextFormat::GetLocaleName
- AFXRENDERTARGET/CD2DTextFormat::IsValid
- AFXRENDERTARGET/CD2DTextFormat::ReCreate
- AFXRENDERTARGET/CD2DTextFormat::m_pTextFormat
dev_langs:
- C++
helpviewer_keywords:
- CD2DTextFormat [MFC], CD2DTextFormat
- CD2DTextFormat [MFC], Create
- CD2DTextFormat [MFC], Destroy
- CD2DTextFormat [MFC], Get
- CD2DTextFormat [MFC], GetFontFamilyName
- CD2DTextFormat [MFC], GetLocaleName
- CD2DTextFormat [MFC], IsValid
- CD2DTextFormat [MFC], ReCreate
- CD2DTextFormat [MFC], m_pTextFormat
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 017267a2b633ee8e0a9c23149fe9d3cb7a8be980
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955472"
---
# <a name="cd2dtextformat-class"></a>Klasa CD2DTextFormat
Otoka dla IDWriteTextFormat.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DTextFormat : public CD2DResource;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|Tworzy obiekt CD2DTextFormat.|  
|[CD2DTextFormat:: ~ CD2DTextFormat](#cd2dtextformat__~cd2dtextformat)|Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D format tekstu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DTextFormat::Create](#create)|Tworzy CD2DTextFormat. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DTextFormat::Destroy](#destroy)|Niszczy obiektu CD2DTextFormat. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DTextFormat::Get](#get)|Zwraca interfejs IDWriteTextFormat|  
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|Pobiera kopię nazwę rodziny czcionek.|  
|[CD2DTextFormat::GetLocaleName](#getlocalename)|Pobiera kopię Nazwa ustawień regionalnych.|  
|[CD2DTextFormat::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DTextFormat::ReCreate](#recreate)|Ponownie tworzy CD2DTextFormat. (Przesłania [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DTextFormat::operator IDWriteTextFormat *](#operator_idwritetextformat_star)|Zwraca interfejs IDWriteTextFormat|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|Wskaźnik do IDWriteTextFormat.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="_dtorcd2dtextformat"></a>  CD2DTextFormat:: ~ CD2DTextFormat  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D format tekstu.  
  
```  
virtual ~CD2DTextFormat();
```  
  
##  <a name="cd2dtextformat"></a>  CD2DTextFormat::CD2DTextFormat  
 Tworzy obiekt CD2DTextFormat.  
  
```  
CD2DTextFormat(
    CRenderTarget* pParentTarget,  
    const CString& strFontFamilyName,  
    FLOAT fontSize,  
    DWRITE_FONT_WEIGHT fontWeight = DWRITE_FONT_WEIGHT_NORMAL,  
    DWRITE_FONT_STYLE fontStyle = DWRITE_FONT_STYLE_NORMAL,  
    DWRITE_FONT_STRETCH fontStretch = DWRITE_FONT_STRETCH_NORMAL,  
    const CString& strFontLocale = _T(""),  
    IDWriteFontCollection* pFontCollection = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentTarget*  
 Wskaźnik do obiektu docelowego renderowania.  
  
 *strFontFamilyName*  
 Cstring — obiekt, który zawiera nazwę rodziny czcionek.  
  
 *fontSize*  
 Rozmiar logiczny czcionki w jednostkach DIP ("pikselach niezależnych od urządzenia"). DIPequals 1/96 cala.  
  
 *fontWeight*  
 Wartość, która wskazuje grubość czcionki dla obiekt tekstu.  
  
 *fontStyle*  
 Wartość, która wskazuje styl czcionki dla obiekt tekstu.  
  
 *fontStretch*  
 Wartość, która wskazuje stretch czcionki dla obiekt tekstu.  
  
 *strFontLocale*  
 Cstring — obiekt, który zawiera Nazwa ustawień regionalnych.  
  
 *pFontCollection*  
 Wskaźnik do obiektu kolekcji czcionki. Gdy jest to wartość NULL, wskazuje kolekcji czcionek systemu.  
  
 *bAutoDestroy*  
 Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).  
  
##  <a name="create"></a>  CD2DTextFormat::Create  
 Tworzy CD2DTextFormat.  
  
```  
virtual HRESULT Create(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="destroy"></a>  CD2DTextFormat::Destroy  
 Niszczy obiektu CD2DTextFormat.  
  
```  
virtual void Destroy();
```  
  
##  <a name="get"></a>  CD2DTextFormat::Get  
 Zwraca interfejs IDWriteTextFormat  
  
```  
IDWriteTextFormat* Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu IDWriteTextFormat lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="getfontfamilyname"></a>  CD2DTextFormat::GetFontFamilyName  
 Pobiera kopię nazwę rodziny czcionek.  
  
```  
CString GetFontFamilyName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Cstring — obiekt, który zawiera nazwę bieżącego rodziny czcionek.  
  
##  <a name="getlocalename"></a>  CD2DTextFormat::GetLocaleName  
 Pobiera kopię Nazwa ustawień regionalnych.  
  
```  
CString GetLocaleName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Cstring — obiekt, który zawiera bieżąca nazwa ustawień regionalnych.  
  
##  <a name="isvalid"></a>  CD2DTextFormat::IsValid  
 Sprawdzanie poprawności zasobów  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zasób jest nieprawidłowy; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_ptextformat"></a>  CD2DTextFormat::m_pTextFormat  
 Wskaźnik do IDWriteTextFormat.  
  
```  
IDWriteTextFormat* m_pTextFormat;  
```  
  
##  <a name="operator_idwritetextformat_star"></a>  CD2DTextFormat::operator IDWriteTextFormat *  
 Zwraca interfejs IDWriteTextFormat  
  
```  
operator IDWriteTextFormat*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu IDWriteTextFormat lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="recreate"></a>  CD2DTextFormat::ReCreate  
 Ponownie tworzy CD2DTextFormat.  
  
```  
virtual HRESULT ReCreate(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
