---
title: Klasa CMFCFilterChunkValueImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::Clear
- AFXWIN/CMFCFilterChunkValueImpl::CopyChunk
- AFXWIN/CMFCFilterChunkValueImpl::CopyFrom
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkGUID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkPID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkType
- AFXWIN/CMFCFilterChunkValueImpl::GetString
- AFXWIN/CMFCFilterChunkValueImpl::GetValue
- AFXWIN/CMFCFilterChunkValueImpl::GetValueNoAlloc
- AFXWIN/CMFCFilterChunkValueImpl::IsValid
- AFXWIN/CMFCFilterChunkValueImpl::SetBoolValue
- AFXWIN/CMFCFilterChunkValueImpl::SetDwordValue
- AFXWIN/CMFCFilterChunkValueImpl::SetFileTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetInt64Value
- AFXWIN/CMFCFilterChunkValueImpl::SetIntValue
- AFXWIN/CMFCFilterChunkValueImpl::SetLongValue
- AFXWIN/CMFCFilterChunkValueImpl::SetSystemTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetTextValue
- AFXWIN/CMFCFilterChunkValueImpl::SetChunk
dev_langs:
- C++
helpviewer_keywords:
- CMFCFilterChunkValueImpl [MFC], CMFCFilterChunkValueImpl
- CMFCFilterChunkValueImpl [MFC], Clear
- CMFCFilterChunkValueImpl [MFC], CopyChunk
- CMFCFilterChunkValueImpl [MFC], CopyFrom
- CMFCFilterChunkValueImpl [MFC], GetChunkGUID
- CMFCFilterChunkValueImpl [MFC], GetChunkPID
- CMFCFilterChunkValueImpl [MFC], GetChunkType
- CMFCFilterChunkValueImpl [MFC], GetString
- CMFCFilterChunkValueImpl [MFC], GetValue
- CMFCFilterChunkValueImpl [MFC], GetValueNoAlloc
- CMFCFilterChunkValueImpl [MFC], IsValid
- CMFCFilterChunkValueImpl [MFC], SetBoolValue
- CMFCFilterChunkValueImpl [MFC], SetDwordValue
- CMFCFilterChunkValueImpl [MFC], SetFileTimeValue
- CMFCFilterChunkValueImpl [MFC], SetInt64Value
- CMFCFilterChunkValueImpl [MFC], SetIntValue
- CMFCFilterChunkValueImpl [MFC], SetLongValue
- CMFCFilterChunkValueImpl [MFC], SetSystemTimeValue
- CMFCFilterChunkValueImpl [MFC], SetTextValue
- CMFCFilterChunkValueImpl [MFC], SetChunk
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1f2fcdedb6b01025b06e4384ec2c32e95d08b6e
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040132"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>Klasa CMFCFilterChunkValueImpl
Jest to klasa, która upraszcza zarówno fragmentu, jak i właściwość logiki pary wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Destructs obiektu.|  
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|Tworzy obiekt.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::Clear](#clear)|Czyści ChunkValue.|  
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|Kopiuje tego fragmentu struktury opisujące właściwości fragmentu.|  
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|Inicjuje wartość fragmentu inne wartości tego parametru.|  
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|Pobiera fragmentu identyfikatora GUID.|  
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|Pobiera fragmentu identyfikatora PID (identyfikator właściwości).|  
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|Pobiera bryłkach typu.|  
|[CMFCFilterChunkValueImpl::GetString](#getstring)|Pobiera wartość ciągu.|  
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|Pobiera wartość jako przydzielony propvariant.|  
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|Wartość zwraca nieprzydzielone (wartość wewnętrznego).|  
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|Sprawdza, czy wartość tej właściwości jest nieprawidłowa lub nie.|  
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|Przeciążone. Ustawia właściwość według klucza na wartość logiczną.|  
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Ustawia właściwość przez klucza DWORD.|  
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|Ustawia właściwość przez klucz do filetime.|  
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Ustawia właściwość przez klucz do wartości typu int64.|  
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Ustawia właściwość przez klucz do int.|  
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|Ustawia właściwość przez klucz do postaci DŁUGIEJ.|  
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|Ustawia właściwość przez klucz do SystemTime.|  
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Ustawia właściwość przez klucz na ciąg Unicode.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Funkcja pomocnika, która ustawia typowe właściwości fragmentu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć, po prostu utworzyć klasę CMFCFilterChunkValueImpl rodzaju prawo  
  
 Przykład:  
  
 Fragmentu CMFCFilterChunkValueImpl;  
  
 hr = fragmentu. SetBoolValue(PKEY_IsAttachment, true);  
  
 lub  
  
 hr = fragmentu. SetFileTimeValue (PKEY_ItemDate, ftLastModified);  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ATL::IFilterChunkValue`  
  
 [CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="clear"></a>  CMFCFilterChunkValueImpl::Clear  
 Czyści ChunkValue.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="cmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl  
 Tworzy obiekt.  
  
```  
CMFCFilterChunkValueImpl();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="_dtorcmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl  
 Destructs obiektu.  
  
```  
virtual ~CMFCFilterChunkValueImpl();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="copychunk"></a>  CMFCFilterChunkValueImpl::CopyChunk  
 Kopiuje tego fragmentu struktury opisujące właściwości fragmentu.  
  
```  
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```  
  
### <a name="parameters"></a>Parametry  
 *pStatChunk*  
 Wskaźnik do wartości docelowej opisujące właściwości fragmentu.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="copyfrom"></a>  CMFCFilterChunkValueImpl::CopyFrom  
 Inicjuje wartość fragmentu inne wartości tego parametru.  
  
```  
void CopyFrom (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>Parametry  
 *pValue*  
 Określa wartość źródła do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getchunkguid"></a>  CMFCFilterChunkValueImpl::GetChunkGUID  
 Pobiera fragmentu identyfikatora GUID.  
  
```  
REFGUID GetChunkGUID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do fragmentów identyfikator GUID.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getchunkpid"></a>  CMFCFilterChunkValueImpl::GetChunkPID  
 Pobiera fragmentu identyfikatora PID (identyfikator właściwości).  
  
```  
DWORD GetChunkPID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość DWORD zawierającą identyfikator właściwości.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getchunktype"></a>  CMFCFilterChunkValueImpl::GetChunkType  
 Pobiera typ fragmentu.  
  
```  
CHUNKSTATE GetChunkType() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość CHUNKSTATE wyliczone, która określa, czy bieżącego fragmentu jest właściwością typu tekst lub typ wartości właściwości.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getstring"></a>  CMFCFilterChunkValueImpl::GetString  
 Pobiera wartość ciągu.  
  
```  
CString &GetString();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg zawierający wartość fragmentu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getvalue"></a>  CMFCFilterChunkValueImpl::GetValue  
 Pobiera wartość jako przydzielony propvariant.  
  
```  
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```  
  
### <a name="parameters"></a>Parametry  
 *ppPropVariant*  
 Gdy funkcja zwraca wartość, ten parametr zawiera wartość fragmentu.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK Jeśli PROPVARIANT została przydzielona pomyślnie, a wartość fragmentu została pomyślnie skopiowana do *ppPropVariant*; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getvaluenoalloc"></a>  CMFCFilterChunkValueImpl::GetValueNoAlloc  
 Zwraca wartość-przydzielone (wewnętrzne wartości).  
  
```  
PROPVARIANT GetValueNoAlloc ();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca bieżącą wartość fragmentu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isvalid"></a>  CMFCFilterChunkValueImpl::IsValid  
 Sprawdza, czy wartość tej właściwości jest nieprawidłowa lub nie.  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli bieżąca wartość fragmentu jest nieprawidłowy; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setboolvalue"></a>  CMFCFilterChunkValueImpl::SetBoolValue  
 Przeciążone. Ustawia właściwość według klucza na wartość logiczną.  
  
```  
HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,  
    BOOL bVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);

 
HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,  
    VARIANT_BOOL bVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>Parametry  
 *PKEY*  
 Określa klucz właściwości.  
  
 *bVal*  
 Określa wartość fragmentu do ustawienia.  
  
 *chunkType*  
 Flagi wskazują, czy ten fragmentu zawiera typ tekstu lub typ wartości właściwości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i odmianą języka skojarzone z fragmentów tekstu. Ustawienia regionalne fragmentu jest używany przez indeksatory dokumentu do wykonywania odpowiednich dzielenia tekstu wyrazów. Jeśli fragmentów nie jest typu tekst ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodne tekstu. Wartość niezerowa oznacza, czy istnieje nie bezpośrednie zgodności.  
  
 *cwcStartSource*  
 Przesunięcie, z którego tekst źródłowy pochodnej fragmentu rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału, która oddziela poprzedniego fragmentu od bieżącego fragmentu. Wartości pochodzą z wyliczania CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setchunk"></a>  CMFCFilterChunkValueImpl::SetChunk  
 Funkcja pomocnika, która ustawia typowe właściwości fragmentu.  
  
```  
HRESULT SetChunk(
    REFPROPERTYKEY pkey,  
    CHUNKSTATE chunkType=CHUNK_VALUE,  
    LCID locale=0,  
    DWORD cwcLenSource=0,  
    DWORD cwcStartSource=0,  
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>Parametry  
 *PKEY*  
 Określa klucz właściwości.  
  
 *chunkType*  
 Flagi wskazują, czy ten fragmentu zawiera typ tekstu lub typ wartości właściwości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i odmianą języka skojarzone z fragmentów tekstu. Ustawienia regionalne fragmentu jest używany przez indeksatory dokumentu do wykonywania odpowiednich dzielenia tekstu wyrazów. Jeśli fragmentów nie jest typu tekst ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodne tekstu. Wartość niezerowa oznacza, czy istnieje nie bezpośrednie zgodności.  
  
 *cwcStartSource*  
 Przesunięcie, z którego tekst źródłowy pochodnej fragmentu rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału, która oddziela poprzedniego fragmentu od bieżącego fragmentu. Wartości pochodzą z wyliczania CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setdwordvalue"></a>  CMFCFilterChunkValueImpl::SetDwordValue  
 Ustaw właściwość przez klucza DWORD.  
  
```  
HRESULT SetDwordValue(
    REFPROPERTYKEY pkey,  
    DWORD dwVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>Parametry  
 *PKEY*  
 Określa klucz właściwości.  
  
 *dwVal*  
 Określa wartość fragmentu do ustawienia.  
  
 *chunkType*  
 Flagi wskazują, czy ten fragmentu zawiera typ tekstu lub typ wartości właściwości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i odmianą języka skojarzone z fragmentów tekstu. Ustawienia regionalne fragmentu jest używany przez indeksatory dokumentu do wykonywania odpowiednich dzielenia tekstu wyrazów. Jeśli fragmentów nie jest typu tekst ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodne tekstu. Wartość niezerowa oznacza, czy istnieje nie bezpośrednie zgodności.  
  
 *cwcStartSource*  
 Przesunięcie, z którego tekst źródłowy pochodnej fragmentu rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału, która oddziela poprzedniego fragmentu od bieżącego fragmentu. Wartości pochodzą z wyliczania CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setfiletimevalue"></a>  CMFCFilterChunkValueImpl::SetFileTimeValue  
 Ustaw właściwość przez klucz do filetime.  
  
```  
HRESULT SetFileTimeValue(
    REFPROPERTYKEY pkey,  
    FILETIME dtVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>Parametry  
 *PKEY*  
 Określa klucz właściwości.  
  
 *dtVal*  
 Określa wartość fragmentu do ustawienia.  
  
 *chunkType*  
 Flagi wskazują, czy ten fragmentu zawiera typ tekstu lub typ wartości właściwości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i odmianą języka skojarzone z fragmentów tekstu. Ustawienia regionalne fragmentu jest używany przez indeksatory dokumentu do wykonywania odpowiednich dzielenia tekstu wyrazów. Jeśli fragmentów nie jest typu tekst ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodne tekstu. Wartość niezerowa oznacza, czy istnieje nie bezpośrednie zgodności.  
  
 *cwcStartSource*  
 Przesunięcie, z którego tekst źródłowy pochodnej fragmentu rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału, która oddziela poprzedniego fragmentu od bieżącego fragmentu. Wartości pochodzą z wyliczania CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setint64value"></a>  CMFCFilterChunkValueImpl::SetInt64Value  
 Ustaw właściwość przez klucz do wartości typu int64.  
  
```  
HRESULT SetInt64Value(
    REFPROPERTYKEY pkey,  
    __int64 nVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>Parametry  
 *PKEY*  
 Określa klucz właściwości.  
  
 *nVal*  
 Określa wartość fragmentu do ustawienia.  
  
 *chunkType*  
 Flagi wskazują, czy ten fragmentu zawiera typ tekstu lub typ wartości właściwości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i odmianą języka skojarzone z fragmentów tekstu. Ustawienia regionalne fragmentu jest używany przez indeksatory dokumentu do wykonywania odpowiednich dzielenia tekstu wyrazów. Jeśli fragmentów nie jest typu tekst ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodne tekstu. Wartość niezerowa oznacza, czy istnieje nie bezpośrednie zgodności.  
  
 *cwcStartSource*  
 Przesunięcie, z którego tekst źródłowy pochodnej fragmentu rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału, która oddziela poprzedniego fragmentu od bieżącego fragmentu. Wartości pochodzą z wyliczania CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setintvalue"></a>  CMFCFilterChunkValueImpl::SetIntValue  
 Ustaw właściwość przez klucz do int.  
  
```  
HRESULT SetIntValue(
    REFPROPERTYKEY pkey,  
    int nVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>Parametry  
 *PKEY*  
 Określa klucz właściwości.  
  
 *nVal*  
 Określa wartość fragmentu do ustawienia.  
  
 *chunkType*  
 Flagi wskazują, czy ten fragmentu zawiera typ tekstu lub typ wartości właściwości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i odmianą języka skojarzone z fragmentów tekstu. Ustawienia regionalne fragmentu jest używany przez indeksatory dokumentu do wykonywania odpowiednich dzielenia tekstu wyrazów. Jeśli fragmentów nie jest typu tekst ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodne tekstu. Wartość niezerowa oznacza, czy istnieje nie bezpośrednie zgodności.  
  
 *cwcStartSource*  
 Przesunięcie, z którego tekst źródłowy pochodnej fragmentu rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału, która oddziela poprzedniego fragmentu od bieżącego fragmentu. Wartości pochodzą z wyliczania CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setlongvalue"></a>  CMFCFilterChunkValueImpl::SetLongValue  
 Ustaw właściwość przez klucz do postaci DŁUGIEJ.  
  
```  
HRESULT SetLongValue(
    REFPROPERTYKEY pkey,  
    long lVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>Parametry  
 *PKEY*  
 Określa klucz właściwości.  
  
 *lVal*  
 Określa wartość fragmentu do ustawienia.  
  
 *chunkType*  
 Flagi wskazują, czy ten fragmentu zawiera typ tekstu lub typ wartości właściwości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i odmianą języka skojarzone z fragmentów tekstu. Ustawienia regionalne fragmentu jest używany przez indeksatory dokumentu do wykonywania odpowiednich dzielenia tekstu wyrazów. Jeśli fragmentów nie jest typu tekst ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodne tekstu. Wartość niezerowa oznacza, czy istnieje nie bezpośrednie zgodności.  
  
 *cwcStartSource*  
 Przesunięcie, z którego tekst źródłowy pochodnej fragmentu rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału, która oddziela poprzedniego fragmentu od bieżącego fragmentu. Wartości pochodzą z wyliczania CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setsystemtimevalue"></a>  CMFCFilterChunkValueImpl::SetSystemTimeValue  
 Ustawia właściwość przez klucz do SystemTime.  
  
```  
HRESULT SetSystemTimeValue(
    REFPROPERTYKEY pkey,  
    const SYSTEMTIME& systemTime,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale=0,  
    DWORD cwcLenSource=0,  
    DWORD cwcStartSource=0,  
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>Parametry  
 *PKEY*  
 Określa klucz właściwości.  
  
 *systemTime*  
 Określa wartość fragmentu do ustawienia.  
  
 *chunkType*  
 Flagi wskazują, czy ten fragmentu zawiera typ tekstu lub typ wartości właściwości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i odmianą języka skojarzone z fragmentów tekstu. Ustawienia regionalne fragmentu jest używany przez indeksatory dokumentu do wykonywania odpowiednich dzielenia tekstu wyrazów. Jeśli fragmentów nie jest typu tekst ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodne tekstu. Wartość niezerowa oznacza, czy istnieje nie bezpośrednie zgodności.  
  
 *cwcStartSource*  
 Przesunięcie, z którego tekst źródłowy pochodnej fragmentu rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału, która oddziela poprzedniego fragmentu od bieżącego fragmentu. Wartości pochodzą z wyliczania CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settextvalue"></a>  CMFCFilterChunkValueImpl::SetTextValue  
 Ustawia właściwość przez klucz na ciąg Unicode.  
  
```  
HRESULT SetTextValue(
    REFPROPERTYKEY pkey,  
    LPCTSTR pszValue,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>Parametry  
 *PKEY*  
 Określa klucz właściwości.  
  
 *pszValue*  
 Określa wartość fragmentu do ustawienia.  
  
 *chunkType*  
 Flagi wskazują, czy ten fragmentu zawiera typ tekstu lub typ wartości właściwości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i odmianą języka skojarzone z fragmentów tekstu. Ustawienia regionalne fragmentu jest używany przez indeksatory dokumentu do wykonywania odpowiednich dzielenia tekstu wyrazów. Jeśli fragmentów nie jest typu tekst ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR, to pole jest ignorowane.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodne tekstu. Wartość niezerowa oznacza, czy istnieje nie bezpośrednie zgodności.  
  
 *cwcStartSource*  
 Przesunięcie, z którego tekst źródłowy pochodnej fragmentu rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału, która oddziela poprzedniego fragmentu od bieżącego fragmentu. Wartości pochodzą z wyliczania CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
