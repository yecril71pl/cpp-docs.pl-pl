---
title: Klasa CD2DTextFormat
ms.date: 11/04/2016
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
ms.openlocfilehash: 9d796ac39ba29e6d286926f4975f8f6d2054e7ac
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297895"
---
# <a name="cd2dtextformat-class"></a>Klasa CD2DTextFormat

Otoka IDWriteTextFormat.

## <a name="syntax"></a>Składnia

```
class CD2DTextFormat : public CD2DResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|Tworzy obiekt CD2DTextFormat.|
|[CD2DTextFormat:: ~ CD2DTextFormat](#cd2dtextformat__~cd2dtextformat)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt format tekstowy D2D.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DTextFormat::Create](#create)|Tworzy CD2DTextFormat. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextFormat::Destroy](#destroy)|Niszczy obiekt CD2DTextFormat. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextFormat::Get](#get)|Zwraca IDWriteTextFormat interfejsu|
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|Pobiera kopię nazwę rodziny czcionek.|
|[CD2DTextFormat::GetLocaleName](#getlocalename)|Pobiera kopię nazwy ustawień regionalnych.|
|[CD2DTextFormat::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextFormat::ReCreate](#recreate)|Ponownie tworzy CD2DTextFormat. (Przesłania [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DTextFormat::operator IDWriteTextFormat *](#operator_idwritetextformat_star)|Zwraca IDWriteTextFormat interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

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

Destruktor. Wywołuje się, kiedy niszczony jest obiekt format tekstowy D2D.

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

*pParentTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

*strFontFamilyName*<br/>
CString obiekt, który zawiera nazwę rodziny czcionek.

*FontSize*<br/>
Logiczne rozmiar czcionki w jednostkach DIP ("pikselach niezależnych od urządzenia"). DIPequals 1/96 cala.

*fontWeight*<br/>
Wartość, która wskazuje grubość czcionki dla tekstu obiektu.

*fontStyle*<br/>
Wartość, która wskazuje styl czcionki dla tekstu obiektu.

*fontStretch*<br/>
Wartość, która wskazuje stretch czcionki dla tekstu obiektu.

*strFontLocale*<br/>
Obiekt CString, który zawiera nazwę ustawień regionalnych.

*pFontCollection*<br/>
Wskaźnik do obiektu kolekcji czcionki. W przypadku wartości NULL wskazuje kolekcji czcionek systemowych.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

##  <a name="create"></a>  CD2DTextFormat::Create

Tworzy CD2DTextFormat.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="destroy"></a>  CD2DTextFormat::Destroy

Niszczy obiekt CD2DTextFormat.

```
virtual void Destroy();
```

##  <a name="get"></a>  CD2DTextFormat::Get

Zwraca IDWriteTextFormat interfejsu

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

Obiekt CString, który zawiera nazwę bieżącej rodziny czcionek.

##  <a name="getlocalename"></a>  CD2DTextFormat::GetLocaleName

Pobiera kopię nazwy ustawień regionalnych.

```
CString GetLocaleName() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt CString, który zawiera bieżącą nazwę ustawień regionalnych.

##  <a name="isvalid"></a>  CD2DTextFormat::IsValid

Sprawdzanie zasobów ważności

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zasób jest ważny; w przeciwnym razie wartość FALSE.

##  <a name="m_ptextformat"></a>  CD2DTextFormat::m_pTextFormat

Wskaźnik do IDWriteTextFormat.

```
IDWriteTextFormat* m_pTextFormat;
```

##  <a name="operator_idwritetextformat_star"></a>  CD2DTextFormat::operator IDWriteTextFormat *

Zwraca IDWriteTextFormat interfejsu

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

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
