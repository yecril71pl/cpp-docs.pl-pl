---
title: Procedury walidacji danych standardowe okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17b99d87db2fee3cf80c25157cdb2b2d2b54903b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376047"
---
# <a name="standard-dialog-data-validation-routines"></a>Standardowe procedury walidacji danych okna dialogowego
W tym temacie wymieniono standardowe procedury walidacji (DDV) danych, używany dla typowych formantów okna dialogowego MFC.  
  
> [!NOTE]
>  Standardowe procedury wymiany danych są definiowane w afxdd_.h pliku nagłówka. Jednak aplikacje powinny zawierać afxwin.h.  
  
### <a name="ddv-functions"></a>Funkcje DDV  
  
|||  
|-|-|  
|[Ddv_maxchars —](#ddv_maxchars)|Sprawdza, czy liczba znaków w wartości danego formantu nie przekracza maksymalnej danego.|  
|[Ddv_minmaxbyte —](#ddv_minmaxbyte)|Sprawdza, czy wartość danego formantu nie przekracza danego **BAJTÓW** zakresu.|  
|[Ddv_minmaxdatetime —](#ddv_minmaxdatetime)|Sprawdza, czy wartość danego formantu nie przekracza zakres wyznaczonym czasie.|  
|[Ddv_minmaxdouble —](#ddv_minmaxdouble)|Sprawdza, czy wartość danego formantu nie przekracza danego **podwójne** zakresu.|  
|[Ddv_minmaxdword —](#ddv_minmaxdword)|Sprawdza, czy wartość danego formantu nie przekracza danego **DWORD** zakresu.|  
|[Ddv_minmaxfloat —](#ddv_minmaxfloat)|Sprawdza, czy wartość danego formantu nie przekracza danego **float** zakresu.|  
|[Ddv_minmaxint —](#ddv_minmaxint)|Sprawdza, czy wartość danego formantu nie przekracza danego **int** zakresu.|  
|[Ddv_minmaxlong —](#ddv_minmaxlong)|Sprawdza, czy wartość danego formantu nie przekracza danego **długi** zakresu.|  
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Sprawdza, czy wartość danego formantu nie przekracza danego **LONGLONG** zakresu.|  
|[Ddv_minmaxmonth —](#ddv_minmaxmonth)|Sprawdza, czy wartość danego formantu nie przekracza zakres podanej daty.|  
|[DDV_MinMaxShort](#ddv_minmaxshort)|Sprawdza, czy wartość danego formantu nie przekracza danego **krótki** zakresu.|  
|[Ddv_minmaxslider —](#ddv_minmaxslider)|Sprawdza, czy wartość formantu suwaka danego mieszczą się w danym.|  
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Sprawdza, czy wartość danego formantu nie przekracza danego **UINT** zakresu.|  
|[Ddv_minmaxunsigned —](#ddv_minmaxuint)|Sprawdza, czy wartość danego formantu znajduje się między dwiema określonymi wartościami.| 
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Sprawdza, czy wartość danego formantu nie przekracza danego **ULONGLONG** zakresu.|  
  

  
##  <a name="ddv_maxchars"></a>  Ddv_maxchars —  
 Wywołanie `DDV_MaxChars` Aby sprawdzić, czy wielkość znaków w formancie skojarzone z *wartość* nie przekracza *nChars*.  
  
```   
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,  
    CString const& value,  
    int nChars); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku formularza lub obiekt widoku formantu, z którym jest sprawdzana poprawność danych.  
  
 `nChars`  
 Maksymalna liczba znaków dozwolona.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxbyte"></a>  Ddv_minmaxbyte —  
 Wywołanie `DDV_MinMaxByte` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* wypada w okresie między `minVal` i `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,  
    BYTE value,  
    BYTE minVal,  
    BYTE maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku formularza lub obiekt widoku formantu, z którym jest sprawdzana poprawność danych.  
  
 `minVal`  
 Minimalna wartość (typu **BAJTÓW**) dozwolone.  
  
 `maxVal`  
 Maksymalna wartość (typu **BAJTÓW**) dozwolone.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxdatetime"></a>  Ddv_minmaxdatetime —  
 Wywołanie `DDV_MinMaxDateTime` Aby sprawdzić, czy wartości daty/godziny w selektora daty i godziny kontroli ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) skojarzone z *refValue* wypada w okresie między `refMinRange` i `refMaxRange`.  
  
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
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku. Nie trzeba usunąć ten obiekt.  
  
 *refValue*  
 Odwołanie do [ctime —](../../atl-mfc-shared/reference/ctime-class.md) lub [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt skojarzony ze zmienną członkowską — okno dialogowe, widoku Formularz lub formant widoku obiektu. Ten obiekt zawiera dane, które ma zostać zweryfikowana.  
  
 `refMinRange`  
 Minimalna dozwolona wartość daty/godziny.  
  
 `refMaxRange`  
 Dozwolona wartość maksymalna daty/godziny.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxdouble"></a>  Ddv_minmaxdouble —  
 Wywołanie `DDV_MinMaxDouble` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* wypada w okresie między `minVal` i `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,  
    double const& value,  
    double minVal,  
    double maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku formularza lub obiekt widoku formantu, z którym jest sprawdzana poprawność danych.  
  
 `minVal`  
 Minimalna wartość (typu **podwójne**) dozwolone.  
  
 `maxVal`  
 Maksymalna wartość (typu **podwójne**) dozwolone.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxdword"></a>  Ddv_minmaxdword —  
 Wywołanie `DDV_MinMaxDWord` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* wypada w okresie między `minVal` i `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,  
    DWORD const& value,  
    DWORD minVal,  
    DWORD maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku formularza lub obiekt widoku formantu, z którym jest sprawdzana poprawność danych.  
  
 `minVal`  
 Minimalna wartość (typu `DWORD`) dozwolone.  
  
 `maxVal`  
 Maksymalna wartość (typu `DWORD`) dozwolone.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxfloat"></a>  Ddv_minmaxfloat —  
 Wywołanie `DDV_MinMaxFloat` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* wypada w okresie między `minVal` i `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,  
    float value,  
    float minVal,  
    float maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku formularza lub obiekt widoku formantu, z którym jest sprawdzana poprawność danych.  
  
 `minVal`  
 Minimalna wartość (typu **float**) dozwolone.  
  
 `maxVal`  
 Maksymalna wartość (typu **float**) dozwolone.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxint"></a>  Ddv_minmaxint —  
 Wywołanie `DDV_MinMaxInt` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* wypada w okresie między `minVal` i `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,  
    int value,  
    int minVal,  
    int maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku formularza lub obiekt widoku formantu, z którym jest sprawdzana poprawność danych.  
  
 `minVal`  
 Minimalna wartość (typu `int`) dozwolone.  
  
 `maxVal`  
 Maksymalna wartość (typu `int`) dozwolone.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxlong"></a>  Ddv_minmaxlong —  
 Wywołanie `DDV_MinMaxLong` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* wypada w okresie między `minVal` i `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,  
    long value,  
    long minVal,  
    long maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku formularza lub obiekt widoku formantu, z którym jest sprawdzana poprawność danych.  
  
 `minVal`  
 Minimalna wartość (typu **długi**) dozwolone.  
  
 `maxVal`  
 Maksymalna wartość (typu **długi**) dozwolone.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxlonglong"></a>  DDV_MinMaxLongLong  
 Wywołanie `DDV_MinMaxLongLong` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* wypada w okresie między `minVal` i `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,  
    LONGLONG value,  
    LONGLONG minVal,  
    LONGLONG maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku formularza lub obiekt widoku formantu, z którym jest sprawdzana poprawność danych.  
  
 `minVal`  
 Minimalna wartość (typu **LONGLONG**) dozwolone.  
  
 `maxVal`  
 Maksymalna wartość (typu **LONGLONG**) dozwolone.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxmonth"></a>  Ddv_minmaxmonth —  
 Wywołanie `DDV_MinMaxMonth` Aby sprawdzić, czy wartość daty/godziny w kalendarzu miesięcznym kontroli ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) skojarzone z *refValue* wypada w okresie między `refMinRange` i `refMaxRange`.  
  
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
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *refValue*  
 Odwołanie do obiektu typu `CTime` lub `COleDateTime` skojarzone ze zmienną członkowską okna dialogowego, widok formularza lub kontrolować obiekt widoku. Ten obiekt zawiera dane, które ma zostać zweryfikowana. To odwołanie podczas obliczania przekazuje MFC `DDV_MinMaxMonth` jest wywoływana.  
  
 `refMinRange`  
 Minimalna dozwolona wartość daty/godziny.  
  
 `refMaxRange`  
 Dozwolona wartość maksymalna daty/godziny.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxshort"></a>  DDV_MinMaxShort  
 Wywołanie `DDV_MinMaxShort` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* wypada w okresie między `minVal` i `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,  
    short value,  
    short minVal,  
    short maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku formularza lub obiekt widoku formantu, z którym jest sprawdzana poprawność danych.  
  
 `minVal`  
 Minimalna wartość (typu **krótki**) dozwolone.  
  
 `maxVal`  
 Maksymalna wartość (typu **krótki**) dozwolone.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxslider"></a>  Ddv_minmaxslider —  
 Wywołanie `DDV_MinMaxSlider` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* wypada w okresie między `minVal` i `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,  
    DWORD value,  
    DWORD minVal,  
    DWORD maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do wartości, które ma zostać zweryfikowana. Ten parametr zawiera lub ustawia bieżącej pozycji przycisku przewijania suwaka.  
  
 `minVal`  
 Minimalna dozwolona wartość.  
  
 `maxVal`  
 Maksymalna dozwolona wartość.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md). Uzyskać informacje o formantach suwaka, zobacz [przy użyciu CSliderCtrl](../../mfc/using-csliderctrl.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxuint"></a>  DDV_MinMaxUInt  
 Wywołanie `DDV_MinMaxUInt` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* wypada w okresie między `minVal` i `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,  
    UINT value,  
    UINT minVal,  
    UINT maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku formularza lub obiekt widoku formantu, z którym jest sprawdzana poprawność danych.  
  
 `minVal`  
 Minimalna wartość (typu **UINT**) dozwolone.  
  
 `maxVal`  
 Maksymalna wartość (typu **UINT**) dozwolone.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddv_minmaxulonglong"></a>  DDV_MinMaxULongLong  
 Wywołanie `DDV_MinMaxULongLong` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* wypada w okresie między `minVal` i `maxVal`.  
  
```   
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,  
    ULONGLONG value,  
    ULONGLONG  minVal ,  
    ULONGLONG  maxVal); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku formularza lub obiekt widoku formantu, z którym jest sprawdzana poprawność danych.  
  
 `minVal`  
 Minimalna wartość (typu **ULONGLONG**) dozwolone.  
  
 `maxVal`  
 Maksymalna wartość (typu **ULONGLONG**) dozwolone.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
    
## <a name="see-also"></a>Zobacz też  
 [Procedury wymiany danych standardowe okno dialogowe](../../mfc/reference/standard-dialog-data-exchange-routines.md)   
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)

 ## <a name="ddvminmaxunsigned"></a>DDV_MinMaxUnsigned
Wywołanie `DDV_MinMaxUnsigned` Aby sprawdzić, czy wartość w formancie skojarzone z *wartość* wypada w okresie między `minVal` i `maxVal`.  
   
### <a name="syntax"></a>Składnia    
```
   void AFXAPI DDV_MinMaxUnsigned(  
       CDataExchange* pDX,  
       unsigned value,  
       unsigned minVal,  
       unsigned maxVal );  
```
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku formularza lub obiekt widoku formantu, z którym jest sprawdzana poprawność danych.  
  
 `minVal`  
 Minimalna wartość (typu **niepodpisane** ) dozwolone.  
  
 `maxVal`  
 Maksymalna wartość (typu **niepodpisane** ) dozwolone.  
   
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../dialog-data-exchange-and-validation.md).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdd_.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [Ddx_slider —](#ddx_slider)   
 [Ddx_fieldslider —](#ddx_fieldslider)
 


