---
title: "Cdataconnection — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
dev_langs:
- C++
helpviewer_keywords:
- CDataConnection class
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2c8e405b95543d170a4e94e39626e9b9793791c7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cdataconnection-class"></a>CDataConnection — Klasa
Zarządza połączenia ze źródłem danych.  
  
## <a name="syntax"></a>Składnia

```cpp
class CDataConnection  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CDataConnection](../../data/oledb/cdataconnection-cdataconnection.md)|Konstruktor. Tworzy i inicjuje `CDataConnection` obiektu.|  
|[Kopiuj](../../data/oledb/cdataconnection-copy.md)|Tworzy kopię istniejącego połączenia danych.|  
|[Otwórz](../../data/oledb/cdataconnection-open.md)|Otwiera połączenie ze źródłem danych przy użyciu ciągu inicjowania.|  
|[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)|Otwiera nową sesję w bieżącym połączeniu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[BOOL — operator](../../data/oledb/cdataconnection-operator-bool.md)|Określa, czy bieżąca sesja jest otwarty.|  
|[bool — operator](../../data/oledb/cdataconnection-operator-bool-ole-db.md)|Określa, czy bieżąca sesja jest otwarty.|  
|[Operator CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)|Zwraca odwołanie do ograniczonego `CDataSource` obiektu.|  
|[Operator CDataSource *](../../data/oledb/cdataconnection-operator-cdatasource-star.md)|Zwraca wskaźnik do zamkniętego `CDataSource` obiektu.|  
|[Operator CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md)|Zwraca odwołanie do ograniczonego `CSession` obiektu.|  
|[Operator CSession *](../../data/oledb/cdataconnection-operator-csession-star.md)|Zwraca wskaźnik do zamkniętego `CSession` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CDataConnection` jest klasą przydatne do tworzenia klientów, ponieważ hermetyzuje niezbędnych obiektów (źródła danych i sesji), a niektóre czynności, które należy wykonać podczas nawiązywania połączenia ze źródłem danych  
  
 Bez `CDataConnection`, należy utworzyć `CDataSource` obiekt, należy wywołać jej [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) metody, następnie utwórz wystąpienie [CSession](../../data/oledb/csession-class.md) obiekt, należy wywołać jej [ Otwórz](../../data/oledb/csession-open.md) metody, następnie utwórz [CCommand](../../data/oledb/ccommand-class.md) obiekt i wywołanie jego **Otwórz*** metody.  
  
 Z `CDataConnection`, wystarczy tylko utworzyć obiektu połączenia, przekaż go ciągu inicjującego, a następnie umożliwia otwieranie polecenia tego połączenia. Jeśli planujesz wielokrotnie przy użyciu połączenia z bazą danych, jest dobrym rozwiązaniem, aby utrzymać otwarte, połączenie i `CDataConnection` oferują wygodny sposób, w tym celu.  
  
> [!NOTE]
>  W przypadku tworzenia aplikacji bazy danych, który musi obsługiwać wiele sesji, będą musieli używać [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)