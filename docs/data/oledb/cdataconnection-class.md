---
title: CDataConnection — Klasa
ms.date: 03/27/2019
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
ms.openlocfilehash: fe954e218a099fa7956748904a4baa89f741c52f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368614"
---
# <a name="cdataconnection-class"></a>CDataConnection — Klasa

Zarządza połączeniem ze źródłem danych.

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
|[Cdataconnection](#cdataconnection)|Konstruktor. Wystąpienia i inicjuje `CDataConnection` obiekt.|
|[Kopii](#copy)|Tworzy kopię istniejącego połączenia danych.|
|[Otwórz](#open)|Otwiera połączenie ze źródłem danych przy użyciu ciągu inicjowania.|
|[OpenNewSession (OpenNewSession)](#opennewsession)|Otwiera nową sesję dla bieżącego połączenia.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator BOOL](#op_bool)|Określa, czy bieżąca sesja jest otwarta, czy nie.|
|[bool operatora](#op_bool_ole)|Określa, czy bieżąca sesja jest otwarta, czy nie.|
|[operator CDataSource&](#op_cdata_amp)|Zwraca odwołanie do obiektu `CDataSource` zawartego.|
|[operator CDataSource*](#op_cdata_star)|Zwraca wskaźnik do obiektu `CDataSource` zawartego.|
|[&CSession operatora](#op_csession_amp)|Zwraca odwołanie do obiektu `CSession` zawartego.|
|[operator CSession*](#op_csession_star)|Zwraca wskaźnik do obiektu `CSession` zawartego.|

## <a name="remarks"></a>Uwagi

`CDataConnection`jest użyteczną klasą do tworzenia klientów, ponieważ hermetyzuje niezbędne obiekty (źródło danych i sesję) oraz część pracy, którą należy wykonać podczas łączenia się ze źródłem danych

Bez `CDataConnection`, trzeba utworzyć `CDataSource` obiekt, wywołać jego [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) metoda, a następnie utworzyć [wystąpienie obiektu CSession,](../../data/oledb/csession-class.md) wywołać jego `Open` [Open](../../data/oledb/csession-open.md) metody, a następnie utworzyć [CCommand](../../data/oledb/ccommand-class.md) obiektu i wywołać jego * metody.

W `CDataConnection`przypadku , wystarczy utworzyć obiekt połączenia, przekazać go ciąg inicjalizacji, a następnie użyć tego połączenia, aby otworzyć polecenia. Jeśli planujesz wielokrotnie używać połączenia z bazą danych, dobrym pomysłem jest, aby połączenie było otwarte i `CDataConnection` zapewnia wygodny sposób, aby to zrobić.

> [!NOTE]
> Jeśli tworzysz aplikację bazy danych, która musi obsługiwać wiele sesji, należy użyć [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a>CDataConnection::CDataConnection

Wystąpienia i inicjuje `CDataConnection` obiekt.

### <a name="syntax"></a>Składnia

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Parametry

*ds*<br/>
[w] Odwołanie do istniejącego połączenia danych.

### <a name="remarks"></a>Uwagi

Pierwsze zastąpienie tworzy nowy `CDataConnection` obiekt z ustawieniami domyślnymi.

Drugie zastąpienie tworzy nowy `CDataConnection` obiekt z ustawieniami równoważnymi określonej przez Ciebie obiektowi połączenia danych.

## <a name="cdataconnectioncopy"></a><a name="copy"></a>CDataConnection::Kopiowanie

Tworzy kopię istniejącego połączenia danych.

### <a name="syntax"></a>Składnia

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Parametry

*ds*<br/>
[w] Odwołanie do istniejącego połączenia danych do skopiowania.

## <a name="cdataconnectionopen"></a><a name="open"></a>CDataConnection::Otwórz

Otwiera połączenie ze źródłem danych przy użyciu ciągu inicjowania.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Parametry

*szInitString*<br/>
[w] Ciąg inicjowania dla źródła danych.

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a>CDataConnection::OpenNewSession

Otwiera nową sesję przy użyciu źródła danych bieżącego obiektu połączenia.

### <a name="syntax"></a>Składnia

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Parametry

*Sesji*<br/>
[w/wyjęcie] Odwołanie do nowego obiektu sesji.

### <a name="remarks"></a>Uwagi

Nowa sesja używa obiektu źródłowego zawierającego dane obiektu bieżącego połączenia jako jego obiektu nadrzędnego i może uzyskać dostęp do wszystkich tych samych informacji co źródło danych.

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a>CDataConnection::operator BOOL

Określa, czy bieżąca sesja jest otwarta, czy nie.

### <a name="syntax"></a>Składnia

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość **BOOL** (MFC typedef). **PRAWDA** oznacza, że bieżąca sesja jest otwarta; **FALSE** oznacza, że bieżąca sesja jest zamknięta.

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a>CDataConnection::operator bool (OLE DB)

Określa, czy bieżąca sesja jest otwarta, czy nie.

### <a name="syntax"></a>Składnia

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość **bool** (typ danych C++). **true** oznacza, że bieżąca sesja jest otwarta; **false** oznacza, że bieżąca sesja jest zamknięta.

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a>CDataConnection::operator CDataSource&amp;

Zwraca odwołanie do obiektu `CDataSource` zawartego.

### <a name="syntax"></a>Składnia

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca odwołanie do `CDataSource` obiektu zawarte, co `CDataConnection` pozwala `CDataSource` przekazać obiekt, w którym oczekiwane jest odwołanie.

### <a name="example"></a>Przykład

Jeśli masz funkcję (na `func` przykład poniżej), która `CDataSource` przyjmuje `CDataSource&` odwołanie, `CDataConnection` można użyć do przekazania obiektu zamiast tego.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a>CDataConnection::operator CDataSource*

Zwraca wskaźnik do obiektu `CDataSource` zawartego.

### <a name="syntax"></a>Składnia

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca wskaźnik do `CDataSource` zawartego obiektu, `CDataConnection` co pozwala `CDataSource` przekazać obiekt, w którym oczekuje się wskaźnika.

Zobacz [operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) przykład użycia.

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a>CDataConnection::operator CSession&amp;

Zwraca odwołanie do obiektu `CSession` zawartego.

### <a name="syntax"></a>Składnia

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca odwołanie do `CSession` obiektu zawarte, co `CDataConnection` pozwala `CSession` przekazać obiekt, w którym oczekiwane jest odwołanie.

### <a name="example"></a>Przykład

Jeśli masz funkcję (na `func` przykład poniżej), która `CSession` przyjmuje `CSession&` odwołanie, `CDataConnection` można użyć do przekazania obiektu zamiast tego.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a>CDataConnection::operator CSession*

Zwraca wskaźnik do obiektu `CSession` zawartego.

### <a name="syntax"></a>Składnia

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca wskaźnik do `CSession` zawartego obiektu, `CDataConnection` co pozwala `CSession` przekazać obiekt, w którym oczekuje się wskaźnika.

### <a name="example"></a>Przykład

Zobacz [&operatora CSession](../../data/oledb/cdataconnection-operator-csession-amp.md) dla przykładu użycia.

## <a name="see-also"></a>Zobacz też

[Szablony dla konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów dla konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
