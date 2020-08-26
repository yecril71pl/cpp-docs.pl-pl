---
title: Standardowe procedury walidacji danych okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 19d1858d67802a7c464a9be783e4c1fb96fe3fae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844486"
---
# <a name="standard-dialog-data-validation-routines"></a>Standardowe procedury walidacji danych okna dialogowego

W tym temacie wymieniono standardowe procedury walidacji danych (DDV) okna dialogowego używane dla wspólnych kontrolek okna dialogowego MFC.

> [!NOTE]
> Standardowe procedury wymiany danych w oknie dialogowym są zdefiniowane w pliku nagłówkowym afxdd_. h. Aplikacje powinny jednak zawierać afxwin. h.

### <a name="ddv-functions"></a>Funkcje DDV

|Nazwa|Opis|
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|Weryfikuje liczbę znaków w danej wartości kontrolki, która nie przekracza podaną wartość maksymalną.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Sprawdza, czy dana wartość kontrolki nie przekracza danego zakresu **bajtów** .|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Sprawdza, czy dana wartość kontrolki nie przekracza danego przedziału czasu.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Weryfikuje daną wartość kontrolki, która nie przekracza danego **`double`** zakresu.|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Sprawdza, czy dana wartość kontrolki nie przekracza podanego zakresu **DWORD** .|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Weryfikuje daną wartość kontrolki, która nie przekracza danego **`float`** zakresu.|
|[DDV_MinMaxInt](#ddv_minmaxint)|Weryfikuje daną wartość kontrolki, która nie przekracza danego **`int`** zakresu.|
|[DDV_MinMaxLong](#ddv_minmaxlong)|Weryfikuje daną wartość kontrolki, która nie przekracza danego **`long`** zakresu.|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Sprawdza, czy dana wartość kontrolki nie przekracza danego zakresu **longlong** .|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Sprawdza, czy dana wartość kontrolki nie przekracza podanego zakresu dat.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|Weryfikuje daną wartość kontrolki, która nie przekracza danego **`short`** zakresu.|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Weryfikuje daną wartość kontrolki suwaka w podanym zakresie.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Sprawdza, czy dana wartość kontrolki nie przekracza danego zakresu **uint** .|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|Sprawdza, czy dana wartość kontrolki przypada między dwoma określonymi wartościami.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Sprawdza, czy dana wartość kontrolki nie przekracza danego zakresu **ULONGLONG** .|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a> DDV_MaxChars

Wywołaj `DDV_MaxChars` , aby sprawdzić, czy ilość znaków w kontrolce skojarzonej z *wartością* nie przekracza wartości *nchar*.

```cpp
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym dane są sprawdzane.

*nChar*<br/>
Maksymalna dozwolona liczba znaków.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a> DDV_MinMaxByte

Wywołaj `DDV_MinMaxByte` , aby sprawdzić, czy wartość w kontrolce skojarzonej z *wartością* należy do zakresu od *minVal* do *maxVal*.

```cpp
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym dane są sprawdzane.

*minVal*<br/>
Dozwolona wartość minimalna (typu BYTE).

*maxVal*<br/>
Maksymalna dozwolona wartość (typu BYTE).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a> DDV_MinMaxDateTime

Wywołaj `DDV_MinMaxDateTime` , aby sprawdzić, czy wartość daty/godziny w kontrolce selektora daty i godziny ( [Korzystanie CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) skojarzonej z *refValue* przypada między *refMinRange* i *refMaxRange*.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek. Nie musisz usuwać tego obiektu.

*refValue*<br/>
Odwołanie do obiektu [CTime](../../atl-mfc-shared/reference/ctime-class.md) lub [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) skojarzonego z zmienną członkowską okna dialogowego, widoku formularza lub obiektu widoku formantu. Ten obiekt zawiera dane, które mają zostać sprawdzone.

*refMinRange*<br/>
Minimalna dozwolona wartość daty/godziny.

*refMaxRange*<br/>
Maksymalna dozwolona wartość daty/godziny.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a> DDV_MinMaxDouble

Wywołaj `DDV_MinMaxDouble` , aby sprawdzić, czy wartość w kontrolce skojarzonej z *wartością* należy do zakresu od *minVal* do *maxVal*.

```cpp
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym dane są sprawdzane.

*minVal*<br/>
Dozwolona wartość minimalna (typu **`double`** ).

*maxVal*<br/>
Maksymalna dozwolona wartość (typu **`double`** ).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a> DDV_MinMaxDWord

Wywołaj `DDV_MinMaxDWord` , aby sprawdzić, czy wartość w kontrolce skojarzonej z *wartością* należy do zakresu od *minVal* do *maxVal*.

```cpp
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym dane są sprawdzane.

*minVal*<br/>
Dozwolona wartość minimalna (typu DWORD).

*maxVal*<br/>
Dozwolona jest wartość maksymalna (typu DWORD).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a> DDV_MinMaxFloat

Wywołaj `DDV_MinMaxFloat` , aby sprawdzić, czy wartość w kontrolce skojarzonej z *wartością* należy do zakresu od *minVal* do *maxVal*.

```cpp
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym dane są sprawdzane.

*minVal*<br/>
Dozwolona wartość minimalna (typu **`float`** ).

*maxVal*<br/>
Maksymalna dozwolona wartość (typu **`float`** ).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a> DDV_MinMaxInt

Wywołaj `DDV_MinMaxInt` , aby sprawdzić, czy wartość w kontrolce skojarzonej z *wartością* należy do zakresu od *minVal* do *maxVal*.

```cpp
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym dane są sprawdzane.

*minVal*<br/>
Dozwolona wartość minimalna (typu **`int`** ).

*maxVal*<br/>
Maksymalna dozwolona wartość (typu **`int`** ).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a> DDV_MinMaxLong

Wywołaj `DDV_MinMaxLong` , aby sprawdzić, czy wartość w kontrolce skojarzonej z *wartością* należy do zakresu od *minVal* do *maxVal*.

```cpp
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym dane są sprawdzane.

*minVal*<br/>
Dozwolona wartość minimalna (typu **`long`** ).

*maxVal*<br/>
Maksymalna dozwolona wartość (typu **`long`** ).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a> DDV_MinMaxLongLong

Wywołaj `DDV_MinMaxLongLong` , aby sprawdzić, czy wartość w kontrolce skojarzonej z *wartością* należy do zakresu od *minVal* do *maxVal*.

```cpp
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym dane są sprawdzane.

*minVal*<br/>
Dozwolona wartość minimalna (typu LONGLONG).

*maxVal*<br/>
Maksymalna dozwolona wartość (typu LONGLONG).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a> DDV_MinMaxMonth

Wywołaj `DDV_MinMaxMonth` , aby sprawdzić, czy wartość daty/godziny w kontrolce Kalendarz miesięczny ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) skojarzona z *refValue* przypada między *refMinRange* i *refMaxRange*.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*refValue*<br/>
Odwołanie do obiektu typu `CTime` lub `COleDateTime` skojarzone z zmienną członkowską okna dialogowego, widoku formularza lub obiektu widoku formantu. Ten obiekt zawiera dane, które mają zostać sprawdzone. MFC przekazuje to odwołanie, gdy `DDV_MinMaxMonth` jest wywoływana.

*refMinRange*<br/>
Minimalna dozwolona wartość daty/godziny.

*refMaxRange*<br/>
Maksymalna dozwolona wartość daty/godziny.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a> DDV_MinMaxShort

Wywołaj `DDV_MinMaxShort` , aby sprawdzić, czy wartość w kontrolce skojarzonej z *wartością* należy do zakresu od *minVal* do *maxVal*.

```cpp
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym dane są sprawdzane.

*minVal*<br/>
Dozwolona wartość minimalna (typu **`short`** ).

*maxVal*<br/>
Maksymalna dozwolona wartość (typu **`short`** ).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a> DDV_MinMaxSlider

Wywołaj `DDV_MinMaxSlider` , aby sprawdzić, czy wartość w kontrolce skojarzonej z *wartością* należy do zakresu od *minVal* do *maxVal*.

```cpp
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do wartości do zweryfikowania. Ten parametr zawiera lub ustawia bieżącą pozycję kciuka kontrolki suwaka.

*minVal*<br/>
Minimalna dozwolona wartość.

*maxVal*<br/>
Maksymalna dozwolona wartość.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać informacje o kontrolkach suwaka, zobacz [using korzystanie CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a> DDV_MinMaxUInt

Wywołaj `DDV_MinMaxUInt` , aby sprawdzić, czy wartość w kontrolce skojarzonej z *wartością* należy do zakresu od *minVal* do *maxVal*.

```cpp
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym dane są sprawdzane.

*minVal*<br/>
Dozwolona wartość minimalna (typu UINT).

*maxVal*<br/>
Maksymalna dozwolona wartość (typu UINT).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a> DDV_MinMaxULongLong

Wywołaj `DDV_MinMaxULongLong` , aby sprawdzić, czy wartość w kontrolce skojarzonej z *wartością* należy do zakresu od *minVal* do *maxVal*.

```cpp
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym dane są sprawdzane.

*minVal*<br/>
Dozwolona wartość minimalna (typu ULONGLONG).

*maxVal*<br/>
Maksymalna dozwolona wartość (typu ULONGLONG).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

Wywołaj `DDV_MinMaxUnsigned` , aby sprawdzić, czy wartość w kontrolce skojarzonej z *wartością* należy do zakresu od *minVal* do *maxVal*.

### <a name="syntax"></a>Składnia

```cpp
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym dane są sprawdzane.

*minVal*<br/>
Dozwolona wartość minimalna (typu **`unsigned`** ).

*maxVal*<br/>
Maksymalna dozwolona wartość (typu **`unsigned`** ).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDV, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdd_. h

## <a name="see-also"></a>Zobacz też

[Standardowe procedury wymiany danych w oknie dialogowym](standard-dialog-data-exchange-routines.md)<br/>
[Makra i Globals](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
