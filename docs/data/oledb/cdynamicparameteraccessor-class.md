---
title: Cdynamicparameteraccessor — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
- CDynamicParameterAccessor::CDynamicParameterAccessor
- CDynamicParameterAccessor.CDynamicParameterAccessor
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
- ATL::CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor.GetParamCount
- GetParamCount
- ATL.CDynamicParameterAccessor.GetParamCount
- GetParamIO
- CDynamicParameterAccessor::GetParamIO
- ATL.CDynamicParameterAccessor.GetParamIO
- CDynamicParameterAccessor.GetParamIO
- ATL::CDynamicParameterAccessor::GetParamIO
- ATL::CDynamicParameterAccessor::GetParamLength
- ATL.CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor::GetParamLength
- GetParamLength
- CDynamicParameterAccessor::GetParamName
- ATL.CDynamicParameterAccessor.GetParamName
- GetParamName
- CDynamicParameterAccessor.GetParamName
- ATL::CDynamicParameterAccessor::GetParamName
- CDynamicParameterAccessor::GetParamStatus
- CDynamicParameterAccessor.GetParamStatus
- ATL.CDynamicParameterAccessor.GetParamStatus
- ATL::CDynamicParameterAccessor::GetParamStatus
- GetParamStatus
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
- CDynamicParameterAccessor.GetParamType
- CDynamicParameterAccessor:GetParamType
- CDynamicParameterAccessor::GetParamType
- ATL.CDynamicParameterAccessor.GetParamType
- GetParamType
- ATL::CDynamicParameterAccessor::GetParamType
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParamLength
- CDynamicParameterAccessor.SetParamLength
- ATL.CDynamicParameterAccessor.SetParamLength
- CDynamicParameterAccessor::SetParamLength
- SetParamLength
- CDynamicParameterAccessor::SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamStatus
- ATL::CDynamicParameterAccessor::SetParamStatus
- CDynamicParameterAccessor.SetParamStatus
- SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
dev_langs:
- C++
helpviewer_keywords:
- CDynamicParameterAccessor class
- CDynamicParameterAccessor class, constructor
- CDynamicParameterAccessor method
- GetParam method
- GetParamCount method
- GetParamIO method
- GetParamLength method
- GetParamName method
- GetParamStatus method
- GetParamString method
- GetParamType method
- SetParam method
- SetParamLength method
- SetParamStatus method
- SetParamString method
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a39e4d600ab5bb209a74ce74dd37af2eb496de0d
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465344"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor — Klasa

Podobnie jak [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) , ale uzyskuje informacje o parametrach określonych przez wywołanie [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) interfejsu.

## <a name="syntax"></a>Składnia

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="requirements"></a>Wymagania

**Nagłówek**: atldbcli.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[CDynamicParameterAccessor](#cdynamicparameteraccessor)|Konstruktor.|
|[GetParam](#getparam)|Pobiera dane parametru z buforu.|
|[GetParamCount](#getparamcount)|Pobiera liczbę parametrów w metodzie dostępu.|
|[GetParamIO](#getparamio)|Określa, czy określony parametr to parametr danych wejściowych lub wyjściowych.|
|[GetParamLength](#getparamlength)|Pobiera długość określonego parametru, które są przechowywane w buforze.|
|[GetParamName](#getparamname)|Pobiera nazwę określonego parametru.|
|[GetParamStatus](#getparamstatus)|Pobiera stan określonego parametru, które są przechowywane w buforze.|
|[GetParamString](#getparamstring)|Pobiera dane ciągu określonego parametru, które są przechowywane w buforze.|
|[GetParamType](#getparamtype)|Pobiera typ danych określony parametr.|
|[SetParam](#setparam)|Ustawia rozmiar buforu dla danych parametrów.|
|[SetParamLength](#setparamlength)|Ustawia długość określonego parametru, które są przechowywane w buforze.|
|[SetParamStatus](#setparamstatus)|Ustawia stan określonego parametru, które są przechowywane w buforze.|
|[SetParamString](#setparamstring)|Ustawia dane ciągu określonego parametru, które są przechowywane w buforze.|

## <a name="remarks"></a>Uwagi

Dostawca musi obsługiwać `ICommandWithParameters` dla użytkownika użyć tej klasy.

Informacje o parametrach znajduje się w buforze tworzone i zarządzane przez tę klasę. Uzyskaj dane parametru z buforu za pomocą [getparam —](../../data/oledb/cdynamicparameteraccessor-getparam.md) i [getparamtype —](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Aby uzyskać przykład pokazująca, jak wykonać procedurę programu SQL Server oraz uzyskać wartości parametrów wyjściowych za pomocą tej klasy, zobacz [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) przykładowy kod przedstawiony w [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) repozytorium w witrynie GitHub.

## <a name="cdynamicparameteraccessor"></a> CDynamicParameterAccessor::CDynamicParameterAccessor
Konstruktor.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
typedef CDynamicParameterAccessor _ParamClass;  
CDynamicParameterAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000 )   
   : CDynamicAccessor(eBlobHandling, nBlobSize )  
```  
  
#### <a name="parameters"></a>Parametry  
 *eBlobHandling*  
 Określa sposób obsługi danych obiektów BLOB. Wartość domyślna to DBBLOBHANDLING_DEFAULT. Zobacz [CDynamicAccessor::SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) opis wartości DBBLOBHANDLINGENUM.  
  
 *nBlobSize*  
 Maksymalny rozmiar obiektu BLOB w bajtach; kolumny danych za pośrednictwem ta wartość jest traktowana jako obiekt BLOB. Wartość domyślna to 8000. Zobacz [CDynamicAccessor::SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) Aby uzyskać szczegółowe informacje.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [CDynamicAccessor::CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) konstruktora, aby uzyskać więcej informacji na temat obsługi obiektów BLOB. 

## <a name="getparam"></a> CDynamicParameterAccessor::GetParam
Pobiera dane typu dla określonego parametru z buforu parametru.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
template <class ctype>bool GetParam(DBORDINAL nParam,   
   ctype* pData) const throw();  

template <class ctype> bool GetParam(TCHAR* pParamName,   
   ctype* pData) const throw();  

void* GetParam(DBORDINAL nParam) const throw();  

void* GetParam(TCHAR* pParamName) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *ctype*  
 Oparte na szablonach parametr, który jest typem danych.  
  
 *nParam*  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowany dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego zamówienia w języku SQL lub wywołanie procedury składowanej. Zobacz [setparam —](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 *pParamName*  
 [in] Nazwa parametru.  
  
 *pData*  
 [out] Wskaźnik do pamięci zawierający dane pobrane z buforu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dla wersji nieszablonową wskazuje pamięci zawierający dane są pobierane z buforu. W przypadku wersji oparte na szablonach, zwraca **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia.  
  
 Użyj `GetParam` można pobrać typu parametru danych z bufora. Użyj [getparamstring —](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) można pobrać dane parametru ciągu z buforu.  

## <a name="getparamcount"></a> CDynamicParameterAccessor::GetParamCount
Pobiera liczbę parametrów przechowywanych w buforze.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
DB_UPARAMS GetParamCount() const throw();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba parametrów.  

## <a name="getparamio"></a> CDynamicParameterAccessor::GetParamIO
Określa, czy określony parametr to parametr danych wejściowych lub wyjściowych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
bool GetParamIO(DBORDINAL nParam,   
   DBPARAMIO* pParamIO) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nParam*  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowany dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego zamówienia w języku SQL lub wywołanie procedury składowanej. Zobacz [setparam —](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 *pParamIO*  
 Wskaźnik na zmienną zawierającą `DBPARAMIO` typu (dane wejściowe lub wyjściowe) określony parametr. Jest zdefiniowany następująco:  
  
```cpp  
typedef DWORD DBPARAMIO;  
  
enum DBPARAMIOENUM {  
    DBPARAMIO_NOTPARAM   = 0,  
    DBPARAMIO_INPUT      = 0x1,  
    DBPARAMIO_OUTPUT     = 0x2  
};  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia.  

## <a name="getparamlength"></a> CDynamicParameterAccessor::GetParamLength
Pobiera długość określonego parametru, które są przechowywane w buforze.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
bool GetParamLength(DBORDINAL nParam,  
   DBLENGTH* pLength);  

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nParam*  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowany dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego zamówienia w języku SQL lub wywołanie procedury składowanej. Zobacz [setparam —](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 *pLength*  
 [out] Wskaźnik do zmiennej, zawierająca długość w bajtach określony parametr.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy zastąpienia zwraca **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia. Drugi musi zostać zastąpiona wskazuje ilość pamięci, zawierająca długość parametru. 

## <a name="getparamname"></a> CDynamicParameterAccessor::GetParamName
Pobiera nazwę określonego parametru.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
LPOLESTR GetParamName(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nParam*  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowany dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego zamówienia w języku SQL lub wywołanie procedury składowanej. Zobacz [setparam —](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa określonego parametru.  

## <a name="getparamstatus"></a> CDynamicParameterAccessor::GetParamStatus
Pobiera stan określonego parametru, które są przechowywane w buforze.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
bool GetParamStatus(DBORDINAL nParam,  
   DBSTATUS* pStatus);  

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nParam*  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowany dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego zamówienia w języku SQL lub wywołanie procedury składowanej. Zobacz [setparam —](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 *pStatus*  
 [out] Wskaźnik do zmiennej, zawierający stan DBSTATUS określony parametr. Informacje o wartościach DBSTATUS, zobacz [stan](/previous-versions/windows/desktop/ms722617\(v=vs.85\)) w *OLE DB Podręcznik programisty*, lub Wyszukaj DBSTATUS w oledb.h.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy zastąpienia zwraca **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia. Drugi musi zostać zastąpiona wskazuje pamięci zawierający stan określonego parametru.

## <a name="getparamstring"></a> CDynamicParameterAccessor::GetParamString
Pobiera dane ciągu określonego parametru, które są przechowywane w buforze.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
bool GetParamString(DBORDINAL nParam,  
   CSimpleStringA& strOutput) throw();

bool GetParamString(DBORDINAL nParam,  
   CSimpleStringW& strOutput) throw();
   
bool GetParamString(DBORDINAL nParam,  
   CHAR* pBuffer,  
   size_t* pMaxLen) throw();

bool GetParamString(DBORDINAL nParam,  
   WCHAR* pBuffer,  
   size_t* pMaxLen) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nParam*  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowany dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego zamówienia w języku SQL lub wywołanie procedury składowanej. Zobacz [setparam —](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 *strOutput*  
 [out] ANSI (`CSimpleStringA`) lub Unicode (`CSimpleStringW`) ciągu danych określony parametr. Należy przekazać do parametru typu `CString`, na przykład:  
  
 [!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]  
  
 *pBuffer*  
 [out] Wskaźnik do ANSI (**CHAR**) lub Unicode (**WCHAR**) ciągu danych określony parametr.  
  
 *pMaxLen*  
 [out] Wskaźnik do rozmiar buforu wskazywany przez *pBuffer* (w postaci, łącznie z zakończenia o wartości NULL).  
  
### <a name="remarks"></a>Uwagi  
 Zwraca **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia.  
  
 Jeśli *pBuffer* ma wartość NULL, ta metoda ustawi wymagany rozmiar buforu w pamięci wskazywany przez *pMaxLen* i zwracają **true** bez kopiowania danych.  
  
 Ta metoda zakończy się niepowodzeniem, jeśli bufor *pBuffer* nie jest wystarczająco duży, aby zawierała cały ciąg.  
  
 Użyj `GetParamString` można pobrać dane parametru ciągu z buforu. Użyj [getparam —](../../data/oledb/cdynamicparameteraccessor-getparam.md) można pobrać typu parametru danych z bufora.  

## <a name="getparamtype"></a> CDynamicParameterAccessor::GetParamType
Pobiera typ danych określony parametr.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
bool GetParamType(DBORDINAL nParam,  
   DBTYPE* pType) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nParam*  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowany dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego zamówienia w języku SQL lub wywołanie procedury składowanej. Zobacz [setparam —](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 *pType*  
 [out] Wskaźnik do zmiennej typu danych określonego parametru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia.  

## <a name="setparam"></a> CDynamicParameterAccessor::SetParam
Ustawia bufor parametru przy użyciu określonych danych (innych niż ciąg).  
  
### <a name="syntax"></a>Składnia  
  
```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,  
   constctype* pData,  
   DBSTATUS status = DBSTATUS_S_OK) throw();  

template <class ctype>  
bool SetParam(TCHAR* pParamName,  
   const ctype* pData,  
   DBSTATUS status = DBSTATUS_S_OK) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *ctype*  
 Oparte na szablonach parametr, który jest typem danych.  
  
 *nParam*  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowany dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego zamówienia w języku SQL lub wywołanie procedury składowanej. Na przykład:  
  
 [!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]  
  
 *pParamName*  
 [in] Nazwa parametru.  
  
 *pData*  
 [in] Wskaźnik do pamięci zawierający dane do zapisania w buforze.  
  
 *status*  
 [in] DBSTATUS stan kolumny. Informacje o wartościach DBSTATUS, zobacz [stan](/previous-versions/windows/desktop/ms722617\(v=vs.85\)) w *OLE DB Podręcznik programisty*, lub Wyszukaj DBSTATUS w oledb.h.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia.  
  
 Użyj `SetParam` można ustawić danych parametrów typu w buforze. Użyj [setparamstring —](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) można ustawić dane parametru ciągu w buforze.  

## <a name="setparamlength"></a> CDynamicParameterAccessor::SetParamLength
Ustawia długość określonego parametru, które są przechowywane w buforze.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
bool SetParamLength(DBORDINAL nParam,  
   DBLENGTH length);  
```  
  
#### <a name="parameters"></a>Parametry  
 *nParam*  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowany dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego zamówienia w języku SQL lub wywołanie procedury składowanej. Zobacz [setparam —](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 *Długość*  
 [in] Długość w bajtach określony parametr.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia. 

## <a name="setparamstatus"></a> CDynamicParameterAccessor::SetParamStatus
Ustawia stan określonego parametru, które są przechowywane w buforze.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
bool SetParamStatus(DBORDINAL nParam,  
   DBSTATUS status);  
```  
  
#### <a name="parameters"></a>Parametry  
 *nParam*  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowany dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego zamówienia w języku SQL lub wywołanie procedury składowanej. Zobacz [setparam —](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 *status*  
 [in] Stan DBSTATUS określony parametr. Informacje o wartościach DBSTATUS, zobacz [stan](/previous-versions/windows/desktop/ms722617\(v=vs.85\)) w *OLE DB Podręcznik programisty*, lub Wyszukaj DBSTATUS w oledb.h.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia. 

## <a name="setparamstring"></a> CDynamicParameterAccessor::SetParamString
Ustawia dane ciągu określonego parametru, które są przechowywane w buforze.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
bool SetParamString(DBORDINAL nParam,   
   constCHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK) throw();bool SetParamString(DBORDINAL nParam,   
   constWCHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nParam*  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowany dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego zamówienia w języku SQL lub wywołanie procedury składowanej. Zobacz [setparam —](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 *pString*  
 [in] Wskaźnik do ANSI (**CHAR**) lub Unicode (**WCHAR**) ciągu danych określony parametr. Zobacz DBSTATUS w oledb.h.  
  
 *status*  
 [in] Stan DBSTATUS określony parametr. Informacje o wartościach DBSTATUS, zobacz [stan](/previous-versions/windows/desktop/ms722617\(v=vs.85\)) w *OLE DB Podręcznik programisty*, lub Wyszukaj DBSTATUS w oledb.h.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca **true** w przypadku powodzenia lub **false** w przypadku niepowodzenia.  
  
 `SetParamString` zakończy się niepowodzeniem, Jeśli spróbujesz ustawić ciąg, który jest większy niż maksymalny rozmiar określony dla *pString*.  
  
 Użyj `SetParamString` można ustawić dane parametru ciągu w buforze. Użyj [setparam —](../../data/oledb/cdynamicparameteraccessor-setparam.md) można ustawić danych parametrów typu w buforze. 

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)  
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)  
[CAccessor, klasa](../../data/oledb/caccessor-class.md)  
[CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)  
[CManualAccessor, klasa](../../data/oledb/cmanualaccessor-class.md)  