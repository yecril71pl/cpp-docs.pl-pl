---
title: Standardowe procedury walidacji danych okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 83e3e215ec8d66321bbac5a4a308b04ef69dc68c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372903"
---
# <a name="standard-dialog-data-validation-routines"></a>Standardowe procedury walidacji danych okna dialogowego

W tym temacie wymieniono procedury sprawdzania poprawności danych (DDV) standardowego okna dialogowego używanego do typowych kontrolek dialogowych MFC.

> [!NOTE]
> Standardowe procedury wymiany danych w oknie dialogowym są zdefiniowane w pliku nagłówka afxdd_.h. Jednak aplikacje powinny zawierać afxwin.h.

### <a name="ddv-functions"></a>Funkcje DDV

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|Weryfikuje liczbę znaków w danej wartości formantu nie przekracza podanego maksimum.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Weryfikuje daną wartość kontrolną nie przekracza danego zakresu **BAJTów.**|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Weryfikuje wartość kontroli danej nie przekracza danego zakresu czasu.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Weryfikuje wartość kontroli danej nie przekracza danego **podwójnego** zakresu.|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Weryfikuje wartość kontroli nie przekracza danego zakresu **DWORD.**|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Weryfikuje wartość kontroli danej nie przekracza danego zakresu **float.**|
|[DDV_MinMaxInt](#ddv_minmaxint)|Weryfikuje daną wartość kontrolną nie przekracza danego zakresu **int.**|
|[DDV_MinMaxLong](#ddv_minmaxlong)|Weryfikuje wartość kontroli danej nie przekracza danego **zakresu.**|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Weryfikuje wartość kontroli danej nie przekracza danego zakresu **LONGLONG.**|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Weryfikuje, że dana wartość kontrolna nie przekracza danego zakresu dat.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|Weryfikuje wartość kontroli nie przekracza danego **krótkiego** zakresu.|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Weryfikuje wartość formantu danego suwaka mieści się w danym zakresie.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Weryfikuje wartość kontroli danej nie przekracza danego zakresu **UINT.**|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|Weryfikuje wartość określonego formantu mieści się między dwiema określonymi wartościami.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Weryfikuje wartość kontroli nie przekracza danego zakresu **ULONGLONG.**|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a>DDV_MaxChars

Wywołanie, `DDV_MaxChars` aby sprawdzić, czy ilość znaków w formancie *skojarzonym* z wartością nie przekracza *nChars*.

```cpp
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, za pomocą którego dane są sprawdzane.

*NChary*<br/>
Maksymalna dozwolona liczba znaków.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a>DDV_MinMaxByte

`DDV_MinMaxByte` Wywołanie, aby sprawdzić, czy wartość w formancie *skojarzonym* z wartością mieści się między *minVal* i *maxVal*.

```cpp
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, za pomocą którego dane są sprawdzane.

*minVal (ł.*<br/>
Dopuszczalna wartość minimalna (typu BYTE).

*maxVal (maxVal)*<br/>
Dopuszczalna wartość maksymalna (typu BYTE).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime

Wywołanie, `DDV_MinMaxDateTime` aby sprawdzić, czy wartość godziny/daty w formancie selektora daty i godziny [(CDateTimeCtrl)](../../mfc/reference/cdatetimectrl-class.md)skojarzonego z *refValue* mieści się między *refMinRange* i *refMaxRange*.

```cpp
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

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku. Nie trzeba usuwać tego obiektu.

*refValue*<br/>
Odwołanie do obiektu [CTime](../../atl-mfc-shared/reference/ctime-class.md) lub [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) skojarzonego ze zmienną członkowną okna dialogowego, widoku formularza lub obiektu widoku sterującego. Ten obiekt zawiera dane, które mają zostać zweryfikowane.

*refMinRange (rozmieszczenie rozmnażeń)*<br/>
Dozwolona minimalna wartość daty/godziny.

*refMaxRange (rozmieszczenie) refMaxRange*<br/>
Maksymalna dozwolona wartość daty/godziny.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble

`DDV_MinMaxDouble` Wywołanie, aby sprawdzić, czy wartość w formancie *skojarzonym* z wartością mieści się między *minVal* i *maxVal*.

```cpp
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, za pomocą którego dane są sprawdzane.

*minVal (ł.*<br/>
Dopuszczalna wartość minimalna (typu **double).**

*maxVal (maxVal)*<br/>
Dopuszczalna wartość maksymalna (typu **double).**

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a>DDV_MinMaxDWord

`DDV_MinMaxDWord` Wywołanie, aby sprawdzić, czy wartość w formancie *skojarzonym* z wartością mieści się między *minVal* i *maxVal*.

```cpp
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, za pomocą którego dane są sprawdzane.

*minVal (ł.*<br/>
Dopuszczalna wartość minimalna (typu DWORD).

*maxVal (maxVal)*<br/>
Dopuszczalna wartość maksymalna (typu DWORD).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat

`DDV_MinMaxFloat` Wywołanie, aby sprawdzić, czy wartość w formancie *skojarzonym* z wartością mieści się między *minVal* i *maxVal*.

```cpp
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, za pomocą którego dane są sprawdzane.

*minVal (ł.*<br/>
Dopuszczalna wartość minimalna **(typu float).**

*maxVal (maxVal)*<br/>
Dopuszczalna maksymalna wartość **(typu float).**

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a>DDV_MinMaxInt

`DDV_MinMaxInt` Wywołanie, aby sprawdzić, czy wartość w formancie *skojarzonym* z wartością mieści się między *minVal* i *maxVal*.

```cpp
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, za pomocą którego dane są sprawdzane.

*minVal (ł.*<br/>
Dopuszczalna wartość minimalna (typu **int).**

*maxVal (maxVal)*<br/>
Dopuszczalna maksymalna wartość (typu **int).**

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a>DDV_MinMaxLong

`DDV_MinMaxLong` Wywołanie, aby sprawdzić, czy wartość w formancie *skojarzonym* z wartością mieści się między *minVal* i *maxVal*.

```cpp
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, za pomocą którego dane są sprawdzane.

*minVal (ł.*<br/>
Dopuszczalna wartość minimalna **(typu długiego).**

*maxVal (maxVal)*<br/>
Dopuszczalna wartość maksymalna **(typu długiego).**

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong

`DDV_MinMaxLongLong` Wywołanie, aby sprawdzić, czy wartość w formancie *skojarzonym* z wartością mieści się między *minVal* i *maxVal*.

```cpp
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, za pomocą którego dane są sprawdzane.

*minVal (ł.*<br/>
Minimalna wartość (typu LONGLONG) dozwolona.

*maxVal (maxVal)*<br/>
Dopuszczalna wartość maksymalna (typu LONGLONG).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth

Wywołanie, `DDV_MinMaxMonth` aby sprawdzić, czy wartość czasu/daty w formancie kalendarza miesiąca ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) skojarzone z *refValue* mieści się między *refMinRange* i *refMaxRange*.

```cpp
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

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*refValue*<br/>
Odwołanie do obiektu typu `CTime` `COleDateTime` lub skojarzonego ze zmienną elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego. Ten obiekt zawiera dane, które mają zostać zweryfikowane. MFC przekazuje to `DDV_MinMaxMonth` odwołanie, gdy jest wywoływana.

*refMinRange (rozmieszczenie rozmnażeń)*<br/>
Dozwolona minimalna wartość daty/godziny.

*refMaxRange (rozmieszczenie) refMaxRange*<br/>
Maksymalna dozwolona wartość daty/godziny.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a>DDV_MinMaxShort

`DDV_MinMaxShort` Wywołanie, aby sprawdzić, czy wartość w formancie *skojarzonym* z wartością mieści się między *minVal* i *maxVal*.

```cpp
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, za pomocą którego dane są sprawdzane.

*minVal (ł.*<br/>
Dopuszczalna wartość minimalna **(typu krótkiego).**

*maxVal (maxVal)*<br/>
Dopuszczalna wartość maksymalna **(typu krótkiego).**

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a>DDV_MinMaxSlider

`DDV_MinMaxSlider` Wywołanie, aby sprawdzić, czy wartość w formancie *skojarzonym* z wartością mieści się między *minVal* i *maxVal*.

```cpp
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do wartości, która ma zostać zweryfikowana. Ten parametr przechowuje lub ustawia bieżącą pozycję kciuka formantu suwaka.

*minVal (ł.*<br/>
Minimalna dozwolona wartość.

*maxVal (maxVal)*<br/>
Maksymalna dozwolona wartość.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać informacje na temat kontrolek suwaków, zobacz [Korzystanie z CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a>DDV_MinMaxUInt

`DDV_MinMaxUInt` Wywołanie, aby sprawdzić, czy wartość w formancie *skojarzonym* z wartością mieści się między *minVal* i *maxVal*.

```cpp
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, za pomocą którego dane są sprawdzane.

*minVal (ł.*<br/>
Minimalna wartość (typu UINT) dozwolona.

*maxVal (maxVal)*<br/>
Dopuszczalna wartość maksymalna (typu UINT).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong

`DDV_MinMaxULongLong` Wywołanie, aby sprawdzić, czy wartość w formancie *skojarzonym* z wartością mieści się między *minVal* i *maxVal*.

```cpp
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, za pomocą którego dane są sprawdzane.

*minVal (ł.*<br/>
Minimalna wartość (typu ULONGLONG) dozwolona.

*maxVal (maxVal)*<br/>
Dopuszczalna wartość maksymalna (typu ULONGLONG).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

`DDV_MinMaxUnsigned` Wywołanie, aby sprawdzić, czy wartość w formancie *skojarzonym* z wartością mieści się między *minVal* i *maxVal*.

### <a name="syntax"></a>Składnia

```cpp
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, za pomocą którego dane są sprawdzane.

*minVal (ł.*<br/>
Dopuszczalna wartość minimalna (typu **niepodpisanego).**

*maxVal (maxVal)*<br/>
Dopuszczalna maksymalna wartość (typu **niepodpisanego).**

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdd_.h

## <a name="see-also"></a>Zobacz też

[Standardowe procedury wymiany danych w oknie dialogowym](standard-dialog-data-exchange-routines.md)<br/>
[Makra i globals](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
