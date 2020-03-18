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
ms.openlocfilehash: e966ce8d0f8b277c0edde2b0b9b345a11c6a964c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442492"
---
# <a name="cdataconnection-class"></a>CDataConnection — Klasa

Zarządza połączeniem ze źródłem danych.

## <a name="syntax"></a>Składnia

```cpp
class CDataConnection
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[CDataConnection](#cdataconnection)|Konstruktor. Tworzy wystąpienia i inicjuje obiekt `CDataConnection`.|
|[Kopiuj](#copy)|Tworzy kopię istniejącego połączenia danych.|
|[Otwórz](#open)|Otwiera połączenie ze źródłem danych przy użyciu ciągu inicjującego.|
|[OpenNewSession](#opennewsession)|Otwiera nową sesję dla bieżącego połączenia.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[wartość logiczna operatora](#op_bool)|Określa, czy bieżąca sesja jest otwarta.|
|[wartość logiczna operatora](#op_bool_ole)|Określa, czy bieżąca sesja jest otwarta.|
|[& operatora CDataSource](#op_cdata_amp)|Zwraca odwołanie do zawartego obiektu `CDataSource`.|
|[CDataSource operatora *](#op_cdata_star)|Zwraca wskaźnik do zawartego obiektu `CDataSource`.|
|[& operatora CSession](#op_csession_amp)|Zwraca odwołanie do zawartego obiektu `CSession`.|
|[CSession operatora *](#op_csession_star)|Zwraca wskaźnik do zawartego obiektu `CSession`.|

## <a name="remarks"></a>Uwagi

`CDataConnection` jest przydatną klasą do tworzenia klientów, ponieważ hermetyzują niezbędne obiekty (Źródło danych i sesja) oraz niektóre zadania, które należy wykonać podczas łączenia ze źródłem danych

Bez `CDataConnection`należy utworzyć obiekt `CDataSource`, wywołać jego metodę [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) , a następnie utworzyć wystąpienie obiektu [CSession](../../data/oledb/csession-class.md) , wywołać metodę [Open](../../data/oledb/csession-open.md) , a następnie utworzyć obiekt [CCommand](../../data/oledb/ccommand-class.md) i wywołać jego `Open`* metody.

Mając `CDataConnection`, wystarczy utworzyć obiekt połączenia, przekazać go jako ciąg inicjujący, a następnie użyć tego połączenia do otwierania poleceń. Jeśli planujesz używać połączenia z bazą danych wielokrotnie, dobrym pomysłem jest pozostawienie otwartego połączenia, a `CDataConnection` zapewnia wygodny sposób.

> [!NOTE]
>  W przypadku tworzenia aplikacji bazy danych, która musi obsługiwać wiele sesji, należy użyć [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).

## <a name="cdataconnection"></a>CDataConnection:: CDataConnection

Tworzy wystąpienia i inicjuje obiekt `CDataConnection`.

### <a name="syntax"></a>Składnia

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Parametry

*domenowe*<br/>
podczas Odwołanie do istniejącego połączenia danych.

### <a name="remarks"></a>Uwagi

Pierwsze zastąpienie powoduje utworzenie nowego obiektu `CDataConnection` z ustawieniami domyślnymi.

Drugie zastąpienie powoduje utworzenie nowego obiektu `CDataConnection` z ustawieniami równoważnymi z określonym obiektem połączenia danych.

## <a name="copy"></a>CDataConnection:: Copy

Tworzy kopię istniejącego połączenia danych.

### <a name="syntax"></a>Składnia

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Parametry

*domenowe*<br/>
podczas Odwołanie do istniejącego połączenia danych do skopiowania.

## <a name="open"></a>CDataConnection:: Open

Otwiera połączenie ze źródłem danych przy użyciu ciągu inicjującego.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Parametry

*szInitString*<br/>
podczas Ciąg inicjujący dla źródła danych.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="opennewsession"></a>CDataConnection:: OpenNewSession

Otwiera nową sesję przy użyciu źródła danych bieżącego obiektu połączenia.

### <a name="syntax"></a>Składnia

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Parametry

*obrad*<br/>
[we/out] Odwołanie do nowego obiektu sesji.

### <a name="remarks"></a>Uwagi

Nowa sesja używa obiektu źródła danych bieżącego obiektu połączenia jako jego elementu nadrzędnego i może uzyskać dostęp do wszystkich tych samych informacji, co źródło danych.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="op_bool"></a>CDataConnection:: operator — BOOL

Określa, czy bieżąca sesja jest otwarta.

### <a name="syntax"></a>Składnia

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość **logiczną** (MFC typedef). **Prawda** oznacza, że bieżąca sesja jest otwarta; **Wartość false** oznacza, że bieżąca sesja jest zamknięta.

## <a name="op_bool_ole"></a>CDataConnection:: operator — bool (OLE DB)

Określa, czy bieżąca sesja jest otwarta.

### <a name="syntax"></a>Składnia

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość **logiczną** (C++ typ danych). **prawda** oznacza, że bieżąca sesja jest otwarta; **wartość false** oznacza, że bieżąca sesja jest zamknięta.

## <a name="op_cdata_amp"></a>CDataConnection:: operator CDataSource&amp;

Zwraca odwołanie do zawartego obiektu `CDataSource`.

### <a name="syntax"></a>Składnia

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca odwołanie do zawartego obiektu `CDataSource`, co pozwala na przekazywanie `CDataConnection` obiektu, w którym oczekiwane jest odwołanie `CDataSource`.

### <a name="example"></a>Przykład

Jeśli masz funkcję (taką jak `func` poniżej), która przyjmuje `CDataSource` odwołanie, możesz użyć `CDataSource&` do przekazania obiektu `CDataConnection`.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="op_cdata_star"></a>CDataConnection:: operator CDataSource *

Zwraca wskaźnik do zawartego obiektu `CDataSource`.

### <a name="syntax"></a>Składnia

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca wskaźnik do zawartego obiektu `CDataSource`, co umożliwia przekazanie obiektu `CDataConnection`, gdzie oczekiwany jest wskaźnik `CDataSource`.

Zobacz [operator CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) dla przykładowego użycia.

## <a name="op_csession_amp"></a>CDataConnection:: operator CSession&amp;

Zwraca odwołanie do zawartego obiektu `CSession`.

### <a name="syntax"></a>Składnia

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca odwołanie do zawartego obiektu `CSession`, co pozwala na przekazywanie `CDataConnection` obiektu, w którym oczekiwane jest odwołanie `CSession`.

### <a name="example"></a>Przykład

Jeśli masz funkcję (taką jak `func` poniżej), która przyjmuje `CSession` odwołanie, możesz użyć `CSession&` do przekazania obiektu `CDataConnection`.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="op_csession_star"></a>CDataConnection:: operator CSession *

Zwraca wskaźnik do zawartego obiektu `CSession`.

### <a name="syntax"></a>Składnia

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca wskaźnik do zawartego obiektu `CSession`, co umożliwia przekazanie obiektu `CDataConnection`, gdzie oczekiwany jest wskaźnik `CSession`.

### <a name="example"></a>Przykład

Zobacz [operator CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md) dla przykładowego użycia.

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)