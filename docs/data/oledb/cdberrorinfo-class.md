---
title: Cdberrorinfo — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- GetCustomErrorObject
- GetErrorInfo
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- GetErrorRecords
- CDBErrorInfo::GetErrorRecords
dev_langs:
- C++
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5bab5334cec33a84abe6b28dc40bd57bf8da432b
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337479"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo — Klasa
Zapewnia obsługę OLE DB wystąpił błąd podczas przetwarzania przy użyciu OLE DB [IErrorRecords](https://msdn.microsoft.com/library/ms718112.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
class CDBErrorInfo  
``` 

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h 
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Getallerrorinfo —](#getallerrorinfo)|Zwraca wszystkie zawarte w rekord błędu informacje o błędzie.|  
|[GetBasicErrorInfo](#getbasicerrorinfo)|Wywołania [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/library/ms723907.aspx) do zwrócenia podstawowe informacje dotyczące określonego błędu.|  
|[GetCustomErrorObject](#getcustomerrorobject)|Wywołania [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/library/ms725417.aspx) aby zwrócić wskaźnik do interfejsu na obiekt błędu niestandardowego.|  
|[GetErrorInfo](#geterrorinfo)|Wywołania [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/library/ms711230.aspx) do zwrócenia `IErrorInfo` wskaźnik interfejsu do określonego rekordu.|  
|[Geterrorparameters —](#geterrorparameters)|Wywołania [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/library/ms715793.aspx) zwracać parametry błędów.|  
|[Geterrorrecords —](#geterrorrecords)|Pobiera rekordy błędów dla określonego obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs rekordy co najmniej jeden błąd użytkownikowi. Wywołaj [CDBErrorInfo::GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) pierwszy, aby uzyskać liczbę rekordów błędów. A następnie wywołania jednej dostępu funkcje, takie jak [CDBErrorInfo::GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md), aby pobrać informacje o błędzie dla każdego rekordu.  
  
## <a name="getallerrorinfo"></a> CDBErrorInfo::GetAllErrorInfo
Zwraca wszystkie typy informacji o błędach zawarte w rekord błędu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetAllErrorInfo(ULONG ulRecordNum,  
   LCID lcid,  BSTR* pbstrDescription,  
   BSTR* pbstrSource = NULL,  
   GUID* pguid = NULL,  
   DWORD* pdwHelpContext = NULL,  
   BSTR* pbstrHelpFile = NULL) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *ulRecordNum*  
 [in] Liczony od zera liczba rekordów, dla której ma zostać zwrócone informacje o błędzie.  
  
 *lcid*  
 [in] Identyfikator ustawień regionalnych dla informacji o błędzie do zwrócenia.  
  
 *pbstrDescription*  
 [out] Wskaźnik do tekst opisu błędu lub wartość NULL, jeśli ustawienia regionalne nie jest obsługiwana. Zobacz uwagi.  
  
 *pbstrSource*  
 [out] Wskaźnik do ciągu zawierającego nazwę składnika, który wygenerował błąd.  
  
 *pguid*  
 [out] Wskaźnik do identyfikatora GUID interfejsu, który zdefiniowany błędu.  
  
 *pdwHelpContext*  
 [out] Wskaźnik do identyfikator kontekstu pomocy dla błędu.  
  
 *pbstrHelpFile*  
 [out] Wskaźnik do ciągu zawierającą ścieżkę do pliku pomocy, który opisuje błąd.  
  
### <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia. Zobacz [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/library/ms711230.aspx) w *OLE DB Podręcznik programisty* dla innych wartości zwracanych.  
  
### <a name="remarks"></a>Uwagi  
 Wartość danych wyjściowych *pbstrDescription* uzyskuje się wewnętrznie przez wywołanie metody `IErrorInfo::GetDescription`, która ustawia wartość null Jeśli ustawienia regionalne nie jest obsługiwany lub jeśli są spełnione oba poniższe warunki:  
  
1.  wartość *lcid* nie jest w Stanach Zjednoczonych Język angielski i  
  
2.  wartość *lcid* jest nie jest równa wartości zwracanej przez GetUserDefaultLCID. 

## <a name="getbasicerrorinfo"></a> CDBErrorInfo::GetBasicErrorInfo
Wywołania [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/library/ms723907.aspx) do zwrócenia podstawowe informacje o błędzie, np. kod powrotny i numer błędu specyficznego dla dostawcy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,   
   ERRORINFO* pErrorInfo) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/library/ms723907.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  

## <a name="getcustomerrorobject"></a> CDBErrorInfo::GetCustomErrorObject
Wywołania [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/library/ms725417.aspx) aby zwrócić wskaźnik do interfejsu na obiekt błędu niestandardowego.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,   
   REFIID riid,IUnknown** ppObject) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/library/ms725417.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  

## <a name="geterrorinfo"></a> CDBErrorInfo::GetErrorInfo
Wywołania [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/library/ms711230.aspx) do zwrócenia [IErrorInfo](https://msdn.microsoft.com/library/ms718112.aspx) wskaźnik interfejsu do określonego rekordu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,   
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/library/ms711230.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  

## <a name="geterrorparameters"></a> CDBErrorInfo::GetErrorParameters
Wywołania [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/library/ms715793.aspx) zwracać parametry błędów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,   
   DISPPARAMS* pdispparams) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/library/ms715793.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  

## <a name="geterrorrecords"></a> CDBErrorInfo::GetErrorRecords
Pobiera rekordy błędów dla określonego obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,   
   const IID& iid,   
   ULONG* pcRecords) throw();  

HRESULT GetErrorRecords(ULONG* pcRecords) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Interfejs do obiektu, dla którego należy pobrać rekordów błędów.  
  
 *IID*  
 [in] Identyfikator IID interfejsu skojarzonego z powodu błędu.  
  
 *pcRecords*  
 [out] Wskaźnik do rekordów błędów liczba (w oparciu o jeden).  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy formularz tej funkcji należy użyć, jeśli chcesz sprawdzić, który interfejs, aby uzyskać informacje o błędzie z. W przeciwnym razie użyj drugiego formularza.  
  
## <a name="see-also"></a>Zobacz też  
 [DBViewer](../../visual-cpp-samples.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)