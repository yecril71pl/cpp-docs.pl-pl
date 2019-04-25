---
title: Standardowe procedury walidacji danych okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 77b08945c99b9e9e2652a40e5710d8c4e89846b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309996"
---
# <a name="standard-dialog-data-validation-routines"></a>Standardowe procedury walidacji danych okna dialogowego

Ten temat zawiera procedury sprawdzania poprawności (DDV) danych standardowe okno dialogowe używane dla typowych formantów okna dialogowego MFC.

> [!NOTE]
>  Procedury wymiany danych w standardowe okno dialogowe, są definiowane w afxdd_.h pliku nagłówka. Jednak aplikacje powinny zawierać afxwin.h.

### <a name="ddv-functions"></a>DDV Functions

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|Sprawdza, czy liczba znaków w wartości danej kontrolki nie przekracza maksymalnej danego.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Sprawdza wartość danej kontrolki nie przekracza danego **BAJTÓW** zakresu.|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Sprawdza, czy wartość danej kontrolki nie przekracza zakres danym momencie.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Sprawdza wartość danej kontrolki nie przekracza danego **double** zakresu.|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Sprawdza wartość danej kontrolki nie przekracza danego **DWORD** zakresu.|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Sprawdza wartość danej kontrolki nie przekracza danego **float** zakresu.|
|[DDV_MinMaxInt](#ddv_minmaxint)|Sprawdza wartość danej kontrolki nie przekracza danego **int** zakresu.|
|[DDV_MinMaxLong](#ddv_minmaxlong)|Sprawdza wartość danej kontrolki nie przekracza danego **długie** zakresu.|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Sprawdza wartość danej kontrolki nie przekracza danego **LONGLONG** zakresu.|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Sprawdza, czy wartość danej kontrolki nie przekracza w danym zakresie dat.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|Sprawdza wartość danej kontrolki nie przekracza danego **krótki** zakresu.|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Sprawdza, czy wartości kontrolki suwaka danego mieści się w danym zakresie.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Sprawdza wartość danej kontrolki nie przekracza danego **UINT** zakresu.|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|Sprawdza, czy wartość danej kontrolki mieści się między dwiema określonymi wartościami.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Sprawdza wartość danej kontrolki nie przekracza danego **ULONGLONG** zakresu.|

##  <a name="ddv_maxchars"></a>  Ddv_maxchars —

Wywołaj `DDV_MaxChars` Aby sprawdzić, czy wielkość znaków w kontrolce skojarzone z *wartość* nie przekracza *nChars*.

```
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub kontrolki widoku obiektu za pomocą którego jest sprawdzana poprawność danych.

*nChars*<br/>
Maksymalna liczba znaków.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxbyte"></a>  Ddv_minmaxbyte —

Wywołaj `DDV_MinMaxByte` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* przypada między *minVal* i *maxVal*.

```
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub kontrolki widoku obiektu za pomocą którego jest sprawdzana poprawność danych.

*minVal*<br/>
Minimalna wartość (typu BYTE) dozwolone.

*maxVal*<br/>
Maksymalna wartość (typu BYTE) dozwolone.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxdatetime"></a>  Ddv_minmaxdatetime —

Wywołaj `DDV_MinMaxDateTime` Aby sprawdzić, czy wartość daty/godziny w selektora daty i godziny sterowania ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) skojarzone z *refValue* przypada między *refMinRange*i *refMaxRange*.

```
void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku. Nie musisz usunąć tego obiektu.

*refValue*<br/>
Odwołanie do [CTime](../../atl-mfc-shared/reference/ctime-class.md) lub [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt skojarzony ze zmienną członkowską, okno dialogowe, widok formularza lub formantu obiekt widoku. Ten obiekt zawiera dane, które mają być weryfikowane.

*refMinRange*<br/>
Minimalna dozwolona wartość daty/godziny.

*refMaxRange*<br/>
Dozwolona wartość maksymalna daty/godziny.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxdouble"></a>  Ddv_minmaxdouble —

Wywołaj `DDV_MinMaxDouble` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* przypada między *minVal* i *maxVal*.

```
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub kontrolki widoku obiektu za pomocą którego jest sprawdzana poprawność danych.

*minVal*<br/>
Minimalna wartość (typu **double**) dozwolone.

*maxVal*<br/>
Maksymalna wartość (typu **double**) dozwolone.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxdword"></a>  Ddv_minmaxdword —

Wywołaj `DDV_MinMaxDWord` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* przypada między *minVal* i *maxVal*.

```
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub kontrolki widoku obiektu za pomocą którego jest sprawdzana poprawność danych.

*minVal*<br/>
Minimalna wartość (typu DWORD) dozwolone.

*maxVal*<br/>
Maksymalna wartość (typu DWORD) dozwolone.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxfloat"></a>  Ddv_minmaxfloat —

Wywołaj `DDV_MinMaxFloat` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* przypada między *minVal* i *maxVal*.

```
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub kontrolki widoku obiektu za pomocą którego jest sprawdzana poprawność danych.

*minVal*<br/>
Minimalna wartość (typu **float**) dozwolone.

*maxVal*<br/>
Maksymalna wartość (typu **float**) dozwolone.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxint"></a>  Ddv_minmaxint —

Wywołaj `DDV_MinMaxInt` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* przypada między *minVal* i *maxVal*.

```
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub kontrolki widoku obiektu za pomocą którego jest sprawdzana poprawność danych.

*minVal*<br/>
Minimalna wartość (typu **int**) dozwolone.

*maxVal*<br/>
Maksymalna wartość (typu **int**) dozwolone.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxlong"></a>  Ddv_minmaxlong —

Wywołaj `DDV_MinMaxLong` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* przypada między *minVal* i *maxVal*.

```
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub kontrolki widoku obiektu za pomocą którego jest sprawdzana poprawność danych.

*minVal*<br/>
Minimalna wartość (typu **długie**) dozwolone.

*maxVal*<br/>
Maksymalna wartość (typu **długie**) dozwolone.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxlonglong"></a>  DDV_MinMaxLongLong

Wywołaj `DDV_MinMaxLongLong` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* przypada między *minVal* i *maxVal*.

```
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub kontrolki widoku obiektu za pomocą którego jest sprawdzana poprawność danych.

*minVal*<br/>
Minimalna wartość (typu LONGLONG) dozwolone.

*maxVal*<br/>
Maksymalna wartość (typu LONGLONG) dozwolone.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxmonth"></a>  Ddv_minmaxmonth —

Wywołaj `DDV_MinMaxMonth` Aby sprawdzić, czy wartość daty/godziny w kalendarza miesięcznego sterowania ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) skojarzony z *refValue* przypada między *refMinRange* i *refMaxRange*.

```
void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*refValue*<br/>
Odwołanie do obiektu typu `CTime` lub `COleDateTime` skojarzone ze zmienną elementu członkowskiego okna dialogowego, widok formularza lub kontrolować obiekt widoku. Ten obiekt zawiera dane, które mają być weryfikowane. Przebiegi MFC to odwołać, kiedy `DDV_MinMaxMonth` jest wywoływana.

*refMinRange*<br/>
Minimalna dozwolona wartość daty/godziny.

*refMaxRange*<br/>
Dozwolona wartość maksymalna daty/godziny.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxshort"></a>  DDV_MinMaxShort

Wywołaj `DDV_MinMaxShort` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* przypada między *minVal* i *maxVal*.

```
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub kontrolki widoku obiektu za pomocą którego jest sprawdzana poprawność danych.

*minVal*<br/>
Minimalna wartość (typu **krótki**) dozwolone.

*maxVal*<br/>
Maksymalna wartość (typu **krótki**) dozwolone.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxslider"></a>  Ddv_minmaxslider —

Wywołaj `DDV_MinMaxSlider` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* przypada między *minVal* i *maxVal*.

```
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do wartości, które ma zostać zweryfikowana. Ten parametr zawiera lub ustawia bieżącej pozycji przycisku przewijania formant suwaka.

*minVal*<br/>
Minimalna dozwolona wartość.

*maxVal*<br/>
Maksymalna dozwolona wartość.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać informacji na temat kontrolki suwaka, zobacz [korzystanie z CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxuint"></a>  DDV_MinMaxUInt

Wywołaj `DDV_MinMaxUInt` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* przypada między *minVal* i *maxVal*.

```
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub kontrolki widoku obiektu za pomocą którego jest sprawdzana poprawność danych.

*minVal*<br/>
Minimalna wartość (typu UINT) dozwolone.

*maxVal*<br/>
Maksymalna wartość (typu UINT) dozwolone.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddv_minmaxulonglong"></a>  DDV_MinMaxULongLong

Wywołaj `DDV_MinMaxULongLong` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* przypada między *minVal* i *maxVal*.

```
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub kontrolki widoku obiektu za pomocą którego jest sprawdzana poprawność danych.

*minVal*<br/>
Minimalna wartość (typu ULONGLONG) dozwolone.

*maxVal*<br/>
Maksymalna wartość (typu ULONGLONG) dozwolone.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddvminmaxunsigned"></a>DDV_MinMaxUnsigned

Wywołaj `DDV_MinMaxUnsigned` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* przypada między *minVal* i *maxVal*.

### <a name="syntax"></a>Składnia

```
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub kontrolki widoku obiektu za pomocą którego jest sprawdzana poprawność danych.

*minVal*<br/>
Minimalna wartość (typu **niepodpisane** ) dozwolone.

*maxVal*<br/>
Maksymalna wartość (typu **niepodpisane** ) dozwolone.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdd_.h

## <a name="see-also"></a>Zobacz także

[Standardowe procedury wymiany danych w oknie dialogowym](standard-dialog-data-exchange-routines.md)<br/>
[Makra i funkcje globalne](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
