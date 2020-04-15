---
title: Klasa CD2DTextFormat
ms.date: 03/27/2019
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
ms.openlocfilehash: f7310fd3ca2ac34df7cc1a99cd5527ea8ba709c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369045"
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
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|Konstruuje obiekt CD2DTextFormat.|
|[CD2DTextFormat::~CD2DTextFormat](#_dtorcd2dtextformat)|Destruktor. Wywoływany, gdy obiekt formatu tekstu D2D jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DTextFormat::Tworzenie](#create)|Tworzy cd2dtextformat. (Zastępuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextFormat::Destroy](#destroy)|Niszczy obiekt CD2DTextFormat. (Zastępuje [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextFormat::Get](#get)|Zwraca interfejs IDWriteTextFormatat|
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|Pobiera kopię nazwy rodziny czcionki.|
|[CD2DTextFormat::GetLocaleName](#getlocalename)|Pobiera kopię nazwy ustawień regionalnych.|
|[CD2DTextFormat::IsValid](#isvalid)|Sprawdza ważność zasobu (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextFormat::Odtwórz](#recreate)|Ponownie tworzy CD2DTextFormat. (Zastępuje [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DTextFormat::operator IDWriteTextFormat*](#operator_idwritetextformat_star)|Zwraca interfejs IDWriteTextFormatat|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|Wskaźnik do IDWriteTextFormat.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DŹródło](../../mfc/reference/cd2dresource-class.md)

[CD2DTeksat](../../mfc/reference/cd2dtextformat-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dtextformatcd2dtextformat"></a><a name="_dtorcd2dtextformat"></a>CD2DTextFormat::~CD2DTextFormat

Destruktor. Wywoływany, gdy obiekt formatu tekstu D2D jest niszczony.

```
virtual ~CD2DTextFormat();
```

## <a name="cd2dtextformatcd2dtextformat"></a><a name="cd2dtextformat"></a>CD2DTextFormat::CD2DTextFormat

Konstruuje obiekt CD2DTextFormat.

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
Wskaźnik do obiektu docelowego renderowania.

*strFontFamilyName*<br/>
Obiekt CString, który zawiera nazwę rodziny czcionek.

*Fontsize*<br/>
Logiczny rozmiar czcionki w jednostkach DIP ("piksel niezależny od urządzenia"). DiPequals 1/96 cala.

*Fontweight*<br/>
Wartość wskazująca wagę czcionki obiektu tekstowego.

*Fontstyle*<br/>
Wartość wskazująca styl czcionki obiektu tekstowego.

*Fontstretch*<br/>
Wartość wskazująca rozciągnięcie czcionki dla obiektu tekstowego.

*strFontLocale (ul.*<br/>
Obiekt CString, który zawiera nazwę ustawień regionalnych.

*pFontCollection (PFontCollection)*<br/>
Wskaźnik do obiektu kolekcji czcionek. Jeśli jest to null, wskazuje kolekcję czcionek systemowych.

*bAutoDestroj*<br/>
Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).

## <a name="cd2dtextformatcreate"></a><a name="create"></a>CD2DTextFormat::Tworzenie

Tworzy cd2dtextformat.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="cd2dtextformatdestroy"></a><a name="destroy"></a>CD2DTextFormat::Destroy

Niszczy obiekt CD2DTextFormat.

```
virtual void Destroy();
```

## <a name="cd2dtextformatget"></a><a name="get"></a>CD2DTextFormat::Get

Zwraca interfejs IDWriteTextFormatat

```
IDWriteTextFormat* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IDWriteTextFormat lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dtextformatgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2DTextFormat::GetFontFamilyName

Pobiera kopię nazwy rodziny czcionki.

```
CString GetFontFamilyName() const;
```

### <a name="return-value"></a>Wartość zwracana

CString obiekt, który zawiera bieżącą nazwę rodziny czcionki.

## <a name="cd2dtextformatgetlocalename"></a><a name="getlocalename"></a>CD2DTextFormat::GetLocaleName

Pobiera kopię nazwy ustawień regionalnych.

```
CString GetLocaleName() const;
```

### <a name="return-value"></a>Wartość zwracana

CString obiekt, który zawiera bieżącą nazwę ustawień regionalnych.

## <a name="cd2dtextformatisvalid"></a><a name="isvalid"></a>CD2DTextFormat::IsValid

Sprawdza ważność zasobu

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zasób jest prawidłowy; w przeciwnym razie FALSE.

## <a name="cd2dtextformatm_ptextformat"></a><a name="m_ptextformat"></a>CD2DTextFormat::m_pTextFormat

Wskaźnik do IDWriteTextFormat.

```
IDWriteTextFormat* m_pTextFormat;
```

## <a name="cd2dtextformatoperator-idwritetextformat"></a><a name="operator_idwritetextformat_star"></a>CD2DTextFormat::operator IDWriteTextFormat*

Zwraca interfejs IDWriteTextFormatat

```
operator IDWriteTextFormat*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IDWriteTextFormat lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dtextformatrecreate"></a><a name="recreate"></a>CD2DTextFormat::Odtwórz

Ponownie tworzy CD2DTextFormat.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
