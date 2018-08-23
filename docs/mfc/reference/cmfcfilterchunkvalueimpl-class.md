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
ms.openlocfilehash: fdce28feddfca0789306a16f8dc6d047dc375120
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42465973"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>Klasa CMFCFilterChunkValueImpl
Jest to klasa, która upraszcza fragment i właściwość logiczną pary wartości.  
  
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
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|Kopiuje ten fragment do struktury opisujących charakterystyki fragmentu.|  
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|Inicjuje tę wartość fragmentów z inną wartość.|  
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|Pobiera fragmentu identyfikatora GUID.|  
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|Pobiera fragmentu identyfikatora PID (właściwość ID).|  
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|Pobiera Podziel typu.|  
|[CMFCFilterChunkValueImpl::GetString](#getstring)|Pobiera wartość ciągu.|  
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|Pobiera wartość jako przydzielony propvariant.|  
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|Zwraca nieprzydzielonym (wartość wewnętrznego) wartość.|  
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|Sprawdza, czy wartość tej właściwości jest nieprawidłowa lub nie.|  
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|Przeciążone. Ustawia właściwość według klucza na wartość logiczną.|  
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Ustawia właściwość według klucza DWORD.|  
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|Ustawia właściwość klucza, aby wartość filetime.|  
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Ustawia właściwość według klucza do int64.|  
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Ustawia właściwość według klucza do int.|  
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|Ustawia właściwość według klucza na wartość typu LONG.|  
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|Ustawia właściwość według klucza do SystemTime.|  
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Ustawia właściwość przez klucz na ciąg Unicode.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Funkcja pomocnicza, która ustawia typowe właściwości fragmentów.|  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć, po prostu Utwórz klasa CMFCFilterChunkValueImpl rodzaj  
  
 Przykład:  
  
 Fragment CMFCFilterChunkValueImpl;  
  
 hr = fragmentów. SetBoolValue(PKEY_IsAttachment, true);  
  
 lub  
  
 hr = fragmentów. SetFileTimeValue (PKEY_ItemDate, ftLastModified);  
  
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
 Kopiuje ten fragment do struktury opisujących charakterystyki fragmentu.  
  
```  
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```  
  
### <a name="parameters"></a>Parametry  
 *pStatChunk*  
 Wskaźnik do wartości docelowej opisujących charakterystyki fragmentów.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="copyfrom"></a>  CMFCFilterChunkValueImpl::CopyFrom  
 Inicjuje tę wartość fragmentów z inną wartość.  
  
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
 Pobiera fragmentu identyfikatora PID (właściwość ID).  
  
```  
DWORD GetChunkPID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość DWORD zawierający identyfikator właściwości.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getchunktype"></a>  CMFCFilterChunkValueImpl::GetChunkType  
 Pobiera typ fragmentu.  
  
```  
CHUNKSTATE GetChunkType() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość wyliczenia CHUNKSTATE, która określa, czy bieżącego fragmentu jest właściwość Typ tekstu lub typu wartości.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getstring"></a>  CMFCFilterChunkValueImpl::GetString  
 Pobiera wartość ciągu.  
  
```  
CString &GetString();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg zawierający wartość fragmentów.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getvalue"></a>  CMFCFilterChunkValueImpl::GetValue  
 Pobiera wartość jako przydzielony propvariant.  
  
```  
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```  
  
### <a name="parameters"></a>Parametry  
 *ppPropVariant*  
 Gdy funkcja zwróci wartość, ten parametr zawiera wartość fragmentów.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli PROPVARIANT została przydzielona pomyślnie, a wartość fragmentów zostały pomyślnie skopiowane do *ppPropVariant*; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getvaluenoalloc"></a>  CMFCFilterChunkValueImpl::GetValueNoAlloc  
 Zwraca wartość nieprzydzielonym (wewnętrzny wartość).  
  
```  
PROPVARIANT GetValueNoAlloc ();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca bieżącą wartość fragmentów.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isvalid"></a>  CMFCFilterChunkValueImpl::IsValid  
 Sprawdza, czy wartość tej właściwości jest nieprawidłowa lub nie.  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli bieżąca wartość fragmentów jest ważny; w przeciwnym razie wartość FALSE.  
  
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
 Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i podjęzyk skojarzone z fragment tekstu. Ustawienia regionalne fragmentów służy indeksatory dokumentu do wykonania odpowiednich wyrazów tekstu. W przypadku typ tekstu ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR fragmentów to pole jest ignorowany.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodnej tekstu. Wartość różną od zera oznacza, że istnieje nie bezpośredniej korespondencji.  
  
 *cwcStartSource*  
 Przesunięcie, w którym tekst źródłowy dla fragmentu pochodnej rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału oddzielający poprzedniego fragmentu od bieżącego fragmentu. Wartości są z wyliczenia CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setchunk"></a>  CMFCFilterChunkValueImpl::SetChunk  
 Funkcja pomocnicza, która ustawia typowe właściwości fragmentów.  
  
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
 Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i podjęzyk skojarzone z fragment tekstu. Ustawienia regionalne fragmentów służy indeksatory dokumentu do wykonania odpowiednich wyrazów tekstu. W przypadku typ tekstu ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR fragmentów to pole jest ignorowany.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodnej tekstu. Wartość różną od zera oznacza, że istnieje nie bezpośredniej korespondencji.  
  
 *cwcStartSource*  
 Przesunięcie, w którym tekst źródłowy dla fragmentu pochodnej rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału oddzielający poprzedniego fragmentu od bieżącego fragmentu. Wartości są z wyliczenia CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setdwordvalue"></a>  CMFCFilterChunkValueImpl::SetDwordValue  
 Ustaw właściwość według klucza DWORD.  
  
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
 Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i podjęzyk skojarzone z fragment tekstu. Ustawienia regionalne fragmentów służy indeksatory dokumentu do wykonania odpowiednich wyrazów tekstu. W przypadku typ tekstu ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR fragmentów to pole jest ignorowany.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodnej tekstu. Wartość różną od zera oznacza, że istnieje nie bezpośredniej korespondencji.  
  
 *cwcStartSource*  
 Przesunięcie, w którym tekst źródłowy dla fragmentu pochodnej rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału oddzielający poprzedniego fragmentu od bieżącego fragmentu. Wartości są z wyliczenia CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setfiletimevalue"></a>  CMFCFilterChunkValueImpl::SetFileTimeValue  
 Ustaw właściwość klucza, aby wartość filetime.  
  
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
 Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i podjęzyk skojarzone z fragment tekstu. Ustawienia regionalne fragmentów służy indeksatory dokumentu do wykonania odpowiednich wyrazów tekstu. W przypadku typ tekstu ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR fragmentów to pole jest ignorowany.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodnej tekstu. Wartość różną od zera oznacza, że istnieje nie bezpośredniej korespondencji.  
  
 *cwcStartSource*  
 Przesunięcie, w którym tekst źródłowy dla fragmentu pochodnej rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału oddzielający poprzedniego fragmentu od bieżącego fragmentu. Wartości są z wyliczenia CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setint64value"></a>  CMFCFilterChunkValueImpl::SetInt64Value  
 Ustaw właściwość według klucza do int64.  
  
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
 Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i podjęzyk skojarzone z fragment tekstu. Ustawienia regionalne fragmentów służy indeksatory dokumentu do wykonania odpowiednich wyrazów tekstu. W przypadku typ tekstu ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR fragmentów to pole jest ignorowany.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodnej tekstu. Wartość różną od zera oznacza, że istnieje nie bezpośredniej korespondencji.  
  
 *cwcStartSource*  
 Przesunięcie, w którym tekst źródłowy dla fragmentu pochodnej rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału oddzielający poprzedniego fragmentu od bieżącego fragmentu. Wartości są z wyliczenia CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setintvalue"></a>  CMFCFilterChunkValueImpl::SetIntValue  
 Ustaw właściwość według klucza do int.  
  
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
 Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i podjęzyk skojarzone z fragment tekstu. Ustawienia regionalne fragmentów służy indeksatory dokumentu do wykonania odpowiednich wyrazów tekstu. W przypadku typ tekstu ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR fragmentów to pole jest ignorowany.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodnej tekstu. Wartość różną od zera oznacza, że istnieje nie bezpośredniej korespondencji.  
  
 *cwcStartSource*  
 Przesunięcie, w którym tekst źródłowy dla fragmentu pochodnej rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału oddzielający poprzedniego fragmentu od bieżącego fragmentu. Wartości są z wyliczenia CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setlongvalue"></a>  CMFCFilterChunkValueImpl::SetLongValue  
 Ustaw właściwość według klucza na wartość typu LONG.  
  
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
 Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i podjęzyk skojarzone z fragment tekstu. Ustawienia regionalne fragmentów służy indeksatory dokumentu do wykonania odpowiednich wyrazów tekstu. W przypadku typ tekstu ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR fragmentów to pole jest ignorowany.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodnej tekstu. Wartość różną od zera oznacza, że istnieje nie bezpośredniej korespondencji.  
  
 *cwcStartSource*  
 Przesunięcie, w którym tekst źródłowy dla fragmentu pochodnej rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału oddzielający poprzedniego fragmentu od bieżącego fragmentu. Wartości są z wyliczenia CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setsystemtimevalue"></a>  CMFCFilterChunkValueImpl::SetSystemTimeValue  
 Ustawia właściwość według klucza do SystemTime.  
  
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
 Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i podjęzyk skojarzone z fragment tekstu. Ustawienia regionalne fragmentów służy indeksatory dokumentu do wykonania odpowiednich wyrazów tekstu. W przypadku typ tekstu ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR fragmentów to pole jest ignorowany.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodnej tekstu. Wartość różną od zera oznacza, że istnieje nie bezpośredniej korespondencji.  
  
 *cwcStartSource*  
 Przesunięcie, w którym tekst źródłowy dla fragmentu pochodnej rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału oddzielający poprzedniego fragmentu od bieżącego fragmentu. Wartości są z wyliczenia CHUNK_BREAKTYPE.  
  
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
 Flagi wskazują, czy ten fragment zawiera typ tekstu lub właściwość typu wartości. Wartości flagi są pobierane z wyliczenia CHUNKSTATE.  
  
 *Ustawienia regionalne*  
 Język i podjęzyk skojarzone z fragment tekstu. Ustawienia regionalne fragmentów służy indeksatory dokumentu do wykonania odpowiednich wyrazów tekstu. W przypadku typ tekstu ani typem wartości o typie danych VT_LPWSTR, VT_LPSTR lub VT_BSTR fragmentów to pole jest ignorowany.  
  
 *cwcLenSource*  
 Długość w znakach tekst źródłowy, z którego pochodzi bieżącego fragmentu. Wartość zero oznacza znak po znaku zgodności między tekst źródłowy i pochodnej tekstu. Wartość różną od zera oznacza, że istnieje nie bezpośredniej korespondencji.  
  
 *cwcStartSource*  
 Przesunięcie, w którym tekst źródłowy dla fragmentu pochodnej rozpoczyna się we fragmencie źródła.  
  
 *chunkBreakType*  
 Typ podziału oddzielający poprzedniego fragmentu od bieżącego fragmentu. Wartości są z wyliczenia CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
