---
title: Zastępowanie ustawień domyślnych usługi dostawcy
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: 4cf3ad1064627f64315822a5045642aa50330d10
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209814"
---
# <a name="overriding-provider-service-defaults"></a>Zastępowanie ustawień domyślnych usługi dostawcy

Wartość rejestru dostawcy dla OLEDB_SERVICES jest zwracana jako wartość domyślna właściwości inicjowania [DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898(v=vs.85)) w obiekcie źródła danych.

Tak długo, jak istnieje wpis rejestru, obiekty dostawcy są agregowane. Użytkownik może zastąpić domyślne ustawienie dostawcy dla włączonych usług, ustawiając właściwość DBPROP_INIT_OLEDBSERVICES przed inicjalizacją. Aby włączyć lub wyłączyć określoną usługę, użytkownik pobiera bieżącą wartość właściwości DBPROP_INIT_OLEDBSERVICES, ustawia lub czyści bit dla konkretnej właściwości, która ma być włączona lub wyłączona, i resetuje właściwość. DBPROP_INIT_OLEDBSERVICES można ustawić bezpośrednio w OLE DB lub w parametrach połączenia przesłanych do obiektu ADO lub `IDataInitialize::GetDatasource`. Odpowiednie wartości w celu włączenia/wyłączenia poszczególnych usług są wymienione w poniższej tabeli.

|Domyślne usługi włączone|DBPROP_INIT_OLEDBSERVICES wartość właściwości|Wartość w parametrach połączenia|
|------------------------------|------------------------------------------------|--------------------------------|
|Wszystkie usługi (wartość domyślna)|DBPROPVAL_OS_ENABLEALL|"OLE DB Services =-1;"|
|Wszystkie z wyjątkiem puli i autorejestrowania|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"OLE DB Services =-4;"|
|Wszystkie z wyjątkiem kursora klienta|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services =-5;"|
|Wszystkie z wyjątkiem puli, autorejestrowania i kursora klienta|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services =-7;"|
|Brak usług|`~DBPROPVAL_OS_ENABLEALL`|"OLE DB Services = 0;"|

Jeśli wpis rejestru nie istnieje dla dostawcy, menedżerów składników nie będą zbierać obiektów dostawcy. Żadne usługi nie będą włączane, nawet jeśli użytkownik jawnie prosi o to.

## <a name="see-also"></a>Zobacz też

[Buforowanie zasobów](/previous-versions/windows/desktop/ms713655(v=vs.85))<br/>
[Jak konsumenci używają puli zasobów](/previous-versions/windows/desktop/ms715907(v=vs.85))<br/>
[Jak dostawcy efektywnie pracują z buforowaniem zasobów](/previous-versions/windows/desktop/ms714906(v=vs.85))<br/>
[Włączanie i wyłączanie usług OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>
