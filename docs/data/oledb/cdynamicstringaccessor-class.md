---
title: Cdynamicstringaccessor — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d74138247bdfd427dd26d1a3d98b9a82dae39e60
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337690"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor — Klasa
Umożliwia dostęp do źródła danych, gdy masz nie znajomości schematu bazy danych (wewnętrzna struktura bazy danych).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
template< typename BaseType, DBTYPEENUM OleDbType >  
class CDynamicStringAccessorT : public CDynamicAccessor  
```  

## <a name="requirements"></a>Wymagania  
 **Nagłówek**: atldbcli.h 

## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetString —](#getstring)|Pobiera dane określonej kolumny jako ciąg.|  
|[Setstring —](#setstring)|Ustawia dane określonej kolumny jako ciąg.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) żąda danych w formacie natywnym zgłoszony przez dostawcę `CDynamicStringAccessor` żądań, że dostawca pobrać wszystkie dane używane z magazynu danych jako dane ciągu. Jest to szczególnie przydatne w przypadku prostych zadań, które nie wymagają obliczenia wartości w magazynie danych, takich jak wyświetlanie lub drukowanie zawartość magazynu danych.  
  
 Natywnego typu danych kolumny w magazynie danych nie ma znaczenia; tak długo, jak dostawca może obsługiwać Konwersja danych, jej będzie dostarczać dane w formacie ciągu. Jeśli dostawca nie obsługuje konwersji z typu danych natywnych na ciąg, (która nie jest często), żądanie wywołania zwróci wartość powodzenia DB_S_ERRORSOCCURED i stan odpowiednia kolumna będą wskazywać problem z konwersją z DBSTATUS_E_CANTCONVERTVALUE.  
  
 Użyj `CDynamicStringAccessor` metody, aby uzyskać informacje o kolumnach. Informacje o kolumnie umożliwia dynamiczne tworzenie metody dostępu w czasie wykonywania.  
  
 Informacje o kolumnach są przechowywane w buforze tworzone i zarządzane przez tę klasę. Uzyskiwanie danych z bufora przy użyciu [GetString —](../../data/oledb/cdynamicstringaccessor-getstring.md), czy zapisać je przy użyciu buforu [setstring —](../../data/oledb/cdynamicstringaccessor-setstring.md).  
  
 Dyskusję na temat i przykłady użycia klas dynamicznej metody dostępu, zobacz [przy użyciu dynamicznych metod dostępu](../../data/oledb/using-dynamic-accessors.md).  

## <a name="getstring"></a> CDynamicStringAccessor::GetString
Pobiera dane określonej kolumny jako ciąg.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();  

BaseType* GetString(const CHAR* pColumnName) const throw();  

BaseType* GetString(const WCHAR* pColumnName) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nColumn*  
 [in] Numer kolumny. Numery kolumn zaczynać od 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieje.  
  
 *pColumnName*  
 [in] Wskaźnik do ciągu znaków, który zawiera nazwę kolumny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wartości ciągu jest pobierana z określonej kolumny. Wartość jest typu `BaseType`, który będzie stanowić **CHAR** lub **WCHAR** w zależności od tego, czy _UNICODE zdefiniowano, czy nie. Zwraca wartość NULL, jeśli nie można odnaleźć określonej kolumny.  
  
### <a name="remarks"></a>Uwagi  
 Drugi musi zostać zastąpiona formularz przyjmuje nazwy kolumny jako ciąg ANSI. Trzeci musi zostać zastąpiona formularz przyjmuje nazwy kolumny jako ciąg Unicode.  
 
## <a name="setstring"></a> CDynamicStringAccessor::SetString
Ustawia dane określonej kolumny jako ciąg.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetString(DBORDINAL nColumn,  
   BaseType* data) throw();  

HRESULT SetString(const CHAR* pColumnName,  
   BaseType* data) throw();  

HRESULT SetString(const WCHAR* pColumnName,  
   BaseType* data) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nColumn*  
 [in] Numer kolumny. Numery kolumn zaczynać od 1. Specjalna wartość 0 odwołuje się do kolumny zakładki, jeśli istnieje.  
  
 *pColumnName*  
 [in] Wskaźnik do ciągu znaków, który zawiera nazwę kolumny.  
  
 *Dane*  
 [in] Wskaźnik do danych ciągu, są zapisywane w określonej kolumnie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wartości ciągu, do którego można ustawić określonej kolumny. Wartość jest typu `BaseType`, który będzie stanowić **CHAR** lub **WCHAR** w zależności od tego, czy _UNICODE zdefiniowano, czy nie.  
  
### <a name="remarks"></a>Uwagi  
 Drugi Zastąp formularz przyjmuje nazwę kolumny jako ciąg ANSI i trzeci Zastąp formularz przyjmuje nazwę kolumny jako ciąg Unicode.  
  
 Jeśli _SECURE_ATL jest zdefiniowana ma wartość różną od zera, jeśli zostanie wygenerowany błąd asercji czasu wykonywania dane wejściowe *danych* ciąg jest dłuższy niż maksymalna dopuszczalna długość kolumny danych występujące w odwołaniu. W przeciwnym razie ciąg wejściowy zostanie obcięty, jeśli przekracza maksymalną dozwoloną długość.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB — Kompendium szablonów konsumentów](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [Klasa CAccessor](../../data/oledb/caccessor-class.md)   
 [Cdynamicparameteraccessor — klasa](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [Cmanualaccessor — klasa](../../data/oledb/cmanualaccessor-class.md)   
 [Cdynamicaccessor — klasa](../../data/oledb/cdynamicaccessor-class.md)   
 [Cdynamicstringaccessora — klasa](../../data/oledb/cdynamicstringaccessora-class.md)   
 [Cdynamicstringaccessorw — klasa](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CXMLAccessor, klasa](../../data/oledb/cxmlaccessor-class.md)