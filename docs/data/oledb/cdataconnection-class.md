---
title: Cdataconnection — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
- CDataConnection.Open
- ATL.CDataConnection.Open
- CDataConnection::Open
- ATL::CDataConnection::Open
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
dev_langs:
- C++
helpviewer_keywords:
- CDataConnection class
- CDataConnection class, constructor
- Copy method
- Open method
- OpenNewSession method
- BOOL operator
- operator bool
- BOOL operator
- operator bool
- CDataSource& operator
- operator & (CDataSource)
- CDataSource* operator
- operator * (CDataSource)
- operator CSession&
- CSession& operator
- operator CSession*
- CSession* operator
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 64e7973c1a818b51173fd4f44458266c10053710
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338262"
---
# <a name="cdataconnection-class"></a>CDataConnection — Klasa
Zarządza połączenia ze źródłem danych.  
  
## <a name="syntax"></a>Składnia

```cpp
class CDataConnection  
```  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h 

## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CDataConnection](#cdataconnection)|Konstruktor. Tworzy i inicjuje `CDataConnection` obiektu.|  
|[Kopiuj](#copy)|Tworzy kopię istniejącego połączenia danych.|  
|[Otwórz](#open)|Otwiera połączenie ze źródłem danych przy użyciu parametrów inicjacji.|  
|[OpenNewSession](#opennewsession)|Otwiera nową sesję w bieżącym połączeniu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[BOOL — operator](#op_bool)|Określa, czy bieżąca sesja jest otwarty.|  
|[bool — operator](#op_bool_ole)|Określa, czy bieżąca sesja jest otwarty.|  
|[Operator CDataSource &](#op_cdata_amp)|Zwraca odwołanie do zamkniętego `CDataSource` obiektu.|  
|[Operator CDataSource *](#op_cdata_star)|Zwraca wskaźnik do zamkniętego `CDataSource` obiektu.|  
|[Operator CSession &](#op_csession_amp)|Zwraca odwołanie do zamkniętego `CSession` obiektu.|  
|[Operator CSession *](#op_csession_star)|Zwraca wskaźnik do zamkniętego `CSession` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CDataConnection` jest klasą przydatne do tworzenia klientów, ponieważ hermetyzuje niezbędnych obiektów (źródła danych i sesji), a niektóre czynności, które należy wykonać podczas nawiązywania połączenia ze źródłem danych  
  
 Bez `CDataConnection`, należy utworzyć `CDataSource` obiektu, wywołaj jej [openfrominitializationstring —](../../data/oledb/cdatasource-openfrominitializationstring.md) metody, następnie utwórz wystąpienie obiektu [CSession](../../data/oledb/csession-class.md) obiektu, wywołaj jej [ Otwórz](../../data/oledb/csession-open.md) metody, następnie utwórz [CCommand](../../data/oledb/ccommand-class.md) obiektu, a następnie wywołać jej `Open`* metody.  
  
 Za pomocą `CDataConnection`, wystarczy tylko utworzyć obiekt połączenia, przekazać go ciąg inicjalizacji, a następnie użyj tego połączenia, aby otworzyć poleceń. Jeśli zamierzasz korzystać z połączenia z bazą danych wielokrotnie, to dobry pomysł, aby utrzymać otwarte połączenia i `CDataConnection` oferuje wygodny sposób, aby to zrobić.  
  
> [!NOTE]
>  Jeśli tworzysz aplikację baza danych, która musi obsługiwać wiele sesji, należy użyć [opennewsession —](../../data/oledb/cdataconnection-opennewsession.md).  

## <a name="#cdataconnection"></a> CDataConnection::CDataConnection
Tworzy i inicjuje `CDataConnection` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
CDataConnection();   
CDataConnection(const CDataConnection &ds);  
```  
  
#### <a name="parameters"></a>Parametry  
 *ds*  
 [in] Odwołanie do istniejącego połączenia danych.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie pierwszy tworzy nową `CDataConnection` obiektu przy użyciu ustawień domyślnych.  
  
 Drugi zastąpienie tworzy nową `CDataConnection` obiektu z odpowiednikiem obiektu połączenia danych, należy określić ustawienia. 

## <a name="#copy"></a> CDataConnection::Copy
Tworzy kopię istniejącego połączenia danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *ds*  
 [in] Odwołanie do istniejącego połączenia danych do skopiowania. 

## <a name="#open"></a> CDataConnection::Open
Otwiera połączenie ze źródłem danych przy użyciu parametrów inicjacji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Open(LPCOLESTR szInitString) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *szInitString*  
 [in] Ciąg inicjalizacji dla źródła danych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  

## <a name="#opennewsession"></a> CDataConnection::OpenNewSession
Zostanie otwarta nowa sesja przy użyciu bieżącego obiektu połączenia źródła danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OpenNewSession(CSession & session) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *Sesji*  
 [/ Ściemnianie] Odwołanie do obiektu nową sesję.  
  
### <a name="remarks"></a>Uwagi  
 Nowa sesja używa obiektu źródła danych zawartej bieżący obiekt połączenia jako klasy nadrzędnej, a może uzyskać dostęp do wszystkich tych samych informacji jako źródło danych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  

## <a name="op_bool"></a> Cdataconnection::operator, wartość logiczna
Określa, czy bieżąca sesja jest otwarty.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
operator BOOL() throw();  
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca **BOOL** wartość (MFC typedef). **Wartość TRUE,** oznacza, że bieżąca sesja jest otwarte **FALSE** oznacza, że bieżąca sesja jest zamknięty. 

## <a name="op_bool_ole"></a> Cdataconnection::operator, wartość logiczna (OLE DB)
Określa, czy bieżąca sesja jest otwarty.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
operator bool() throw();  
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca **bool** wartości (typu C++ danych). **wartość true,** oznacza, że bieżąca sesja jest otwarte **false** oznacza, że bieżąca sesja jest zamknięty.  

## <a name="op_cdata_amp"></a> CDataConnection::operator CDataSource&amp;
Zwraca odwołanie do zamkniętego `CDataSource` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
operator const CDataSource&() throw();  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten operator zwraca odwołanie do zamkniętego `CDataSource` obiektu, dzięki czemu możesz przekazać `CDataConnection` obiektu gdzie `CDataSource` Oczekiwano odwołania.  
  
### <a name="example"></a>Przykład  
 W przypadku funkcji (takich jak `func` poniżej) przyjmującej `CDataSource` odwołania, można użyć `CDataSource&` do przekazania `CDataConnection` zamiast tego obiektu.  
  
 [!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)] 

## <a name="op_cdata_star"></a> CDataConnection::operator CDataSource *
Zwraca wskaźnik do zamkniętego `CDataSource` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
operator const CDataSource*() throw();  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten operator zwraca wskaźnik do zamkniętego `CDataSource` obiektu, dzięki czemu możesz przekazać `CDataConnection` obiektu gdzie `CDataSource` oczekuje wskaźnika.  
  
 Zobacz [operator CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) na przykład użycia.  

## <a name="op_csession_amp"></a> CDataConnection::operator CSession&amp;
Zwraca odwołanie do zamkniętego `CSession` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
operator const CSession&();  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten operator zwraca odwołanie do zamkniętego `CSession` obiektu, dzięki czemu możesz przekazać `CDataConnection` obiektu gdzie `CSession` Oczekiwano odwołania.  
  
### <a name="example"></a>Przykład  
 W przypadku funkcji (takich jak `func` poniżej) przyjmującej `CSession` odwołania, można użyć `CSession&` do przekazania `CDataConnection` zamiast tego obiektu.  
  
 [!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]  

## <a name="op_csession_star"></a> CDataConnection::operator CSession *
Zwraca wskaźnik do zamkniętego `CSession` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
operator const CSession*() throw();  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten operator zwraca wskaźnik do zamkniętego `CSession` obiektu, dzięki czemu możesz przekazać `CDataConnection` obiektu gdzie `CSession` oczekuje wskaźnika.  
  
### <a name="example"></a>Przykład  
 Zobacz [operator CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md) na przykład użycia.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)