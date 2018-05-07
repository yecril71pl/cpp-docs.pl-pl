---
title: Cdatasource — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
dev_langs:
- C++
helpviewer_keywords:
- CDataSource class
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7835cd7401c13ab167a9236db4f7e2fc98f3e175
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdatasource-class"></a>CDataSource — Klasa
Odnosi się do obiektu źródła danych OLE DB, który reprezentuje połączenie za pośrednictwem dostawcy źródła danych.  
  
## <a name="syntax"></a>Składnia

```cpp
class CDataSource  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Zamknij](../../data/oledb/cdatasource-close.md)|Zamyka połączenie.|  
|[GetInitializationString](../../data/oledb/cdatasource-getinitializationstring.md)|Pobiera ciąg inicjowania źródła danych, która jest obecnie otwarta.|  
|[GetProperties](../../data/oledb/cdatasource-getproperties.md)|Pobiera wartości właściwości obecnie połączonego źródła danych.|  
|[GetProperty](../../data/oledb/cdatasource-getproperty.md)|Pobiera wartość jednej właściwości aktualnie ustawione dla połączonego źródła danych.|  
|[Otwórz](../../data/oledb/cdatasource-open.md)|Tworzy połączenie dostawcy (źródła danych) przy użyciu **CLSID**, **ProgID**, lub `CEnumerator` moniker dostarczony przez obiekt wywołujący.|  
|[OpenFromFileName](../../data/oledb/cdatasource-openfromfilename.md)|Otwiera źródło danych z pliku określonego przez nazwę pliku dostarczone przez użytkownika.|  
|[OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)|Otwiera określona przez ciąg inicjowania źródła danych.|  
|[OpenWithPromptFileName](../../data/oledb/cdatasource-openwithpromptfilename.md)|Umożliwia użytkownikowi wybranie plik łącza danych utworzonego wcześniej, aby otworzyć odpowiadającego jej źródła danych.|  
|[OpenWithServiceComponents](../../data/oledb/cdatasource-openwithservicecomponents.md)|Otwiera obiekt źródła danych za pomocą okna dialogowego Łącze danych.|  
  
## <a name="remarks"></a>Uwagi  
 Co najmniej jednej sesji bazy danych można tworzyć dla jednego połączenia. Sesje te są reprezentowane przez `CSession`. Należy wywołać [CDataSource::Open](../../data/oledb/cdatasource-open.md) do otwierania połączenia przed utworzeniem sesji z `CSession::Open`.  
  
 Przykład sposobu użycia `CDataSource`, zobacz [CatDB](../../visual-cpp-samples.md) próbki.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)