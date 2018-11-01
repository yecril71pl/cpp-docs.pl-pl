---
title: Klasa CD2DTextLayout
ms.date: 11/04/2016
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
ms.openlocfilehash: 378c96622144a4acac27785cef844f0c1d21b98b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630948"
---
# <a name="cd2dtextlayout-class"></a>Klasa CD2DTextLayout

Otoka IDWriteTextLayout.

## <a name="syntax"></a>Składnia

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|Tworzy obiekt CD2DTextLayout.|
|[CD2DTextLayout:: ~ CD2DTextLayout](#cd2dtextlayout__~cd2dtextlayout)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt układu tekstu D2D.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DTextLayout::Create](#create)|Tworzy CD2DTextLayout. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextLayout::Destroy](#destroy)|Niszczy obiekt CD2DTextLayout. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextLayout::Get](#get)|Zwraca IDWriteTextLayout interfejsu|
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|Kopiuje nazwy rodziny czcionek tekstu w określonej pozycji.|
|[CD2DTextLayout::GetLocaleName](#getlocalename)|Pobiera nazwę ustawień regionalnych tekstu w określonej pozycji.|
|[CD2DTextLayout::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextLayout::ReCreate](#recreate)|Ponownie tworzy CD2DTextLayout. (Przesłania [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|Nazwa rodziny czcionek zakończony znakiem null zestawów, dla tekstu w zakresie określony tekst|
|[CD2DTextLayout::SetLocaleName](#setlocalename)|Ustawia nazwę ustawień regionalnych dla tekstu w zakresie określony tekst|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DTextLayout::operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|Zwraca IDWriteTextLayout interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|Wskaźnik do IDWriteTextLayout.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="_dtorcd2dtextlayout"></a>  CD2DTextLayout:: ~ CD2DTextLayout

Destruktor. Wywołuje się, kiedy niszczony jest obiekt układu tekstu D2D.

```
virtual ~CD2DTextLayout();
```

##  <a name="cd2dtextlayout"></a>  CD2DTextLayout::CD2DTextLayout

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

*pParentTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

*strText*<br/>
Obiekt CString, który zawiera ciąg, aby utworzyć nowy obiekt CD2DTextLayout.

*textFormat*<br/>
Obiekt CString, który zawiera formatu do zastosowania do ciągu.

*sizeMax*<br/>
Rozmiar pola układu.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

##  <a name="create"></a>  CD2DTextLayout::Create

Tworzy CD2DTextLayout.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="destroy"></a>  CD2DTextLayout::Destroy

Niszczy obiekt CD2DTextLayout.

```
virtual void Destroy();
```

##  <a name="get"></a>  CD2DTextLayout::Get

Zwraca IDWriteTextLayout interfejsu

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IDWriteTextLayout lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="getfontfamilyname"></a>  CD2DTextLayout::GetFontFamilyName

Kopiuje nazwy rodziny czcionek tekstu w określonej pozycji.

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Parametry

*currentPosition*<br/>
Położenie tekstu do sprawdzenia.

*TextRange*<br/>
Zakres tekstu, który ma taką samą formatowania jako tekst w miejscu określonym przez currentPosition. Oznacza to, że działanie jest dokładne formatowanie jako pozycja określony, w tym między innymi nazwę rodziny czcionek.

### <a name="return-value"></a>Wartość zwracana

Obiekt CString, który zawiera nazwę bieżącej rodziny czcionek.

##  <a name="getlocalename"></a>  CD2DTextLayout::GetLocaleName

Pobiera nazwę ustawień regionalnych tekstu w określonej pozycji.

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Parametry

*currentPosition*<br/>
Położenie tekstu do wglądu.

*TextRange*<br/>
Zakres tekstu, który ma taką samą formatowania jako tekst w miejscu określonym przez currentPosition. Oznacza to, że działanie jest dokładne formatowanie jako pozycja określony, w tym między innymi do nazwy ustawień regionalnych.

### <a name="return-value"></a>Wartość zwracana

Obiekt CString, który zawiera bieżącą nazwę ustawień regionalnych.

##  <a name="isvalid"></a>  CD2DTextLayout::IsValid

Sprawdzanie zasobów ważności

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zasób jest ważny; w przeciwnym razie wartość FALSE.

##  <a name="m_ptextlayout"></a>  CD2DTextLayout::m_pTextLayout

Wskaźnik do IDWriteTextLayout.

```
IDWriteTextLayout* m_pTextLayout;
```

##  <a name="operator_idwritetextlayout_star"></a>  CD2DTextLayout::operator IDWriteTextLayout *

Zwraca IDWriteTextLayout interfejsu

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IDWriteTextLayout lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="recreate"></a>  CD2DTextLayout::ReCreate

Ponownie tworzy CD2DTextLayout.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="setfontfamilyname"></a>  CD2DTextLayout::SetFontFamilyName

Nazwa rodziny czcionek zakończony znakiem null zestawów, dla tekstu w zakresie określony tekst

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Parametry

*pwzFontFamilyName*<br/>
Nazwa rodziny czcionek, która ma zastosowanie do cały ciąg tekstowy w zakresie określonym przez textRange

*TextRange*<br/>
Zakres tekstu, którego dotyczy ta zmiana

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE

##  <a name="setlocalename"></a>  CD2DTextLayout::SetLocaleName

Ustawia nazwę ustawień regionalnych dla tekstu w zakresie określony tekst

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Parametry

*pwzLocaleName*<br/>
Ciąg zakończony znakiem null ustawienia regionalne nazwy

*TextRange*<br/>
Zakres tekstu, którego dotyczy ta zmiana

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
