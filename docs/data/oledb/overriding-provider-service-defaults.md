---
title: Zastępowanie ustawień domyślnych usługi dostawcy
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: a9f8eb1c96c40336f39f14fe1a0ee29d60efd003
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265220"
---
# <a name="overriding-provider-service-defaults"></a>Zastępowanie ustawień domyślnych usługi dostawcy

Wartość rejestru dostawcy dla OLEDB_SERVICES jest zwracana jako wartość domyślna dla [DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898) inicjowania właściwości obiektu źródła danych.

Tak długo, jak istnieje wpis rejestru, obiektów dostawcy są agregowane. Użytkownik może przesłonić ustawienia usługi włączone przez ustawienie właściwości DBPROP_INIT_OLEDBSERVICES przed zainicjowaniem domyślnego dostawcy. Aby włączyć lub wyłączyć określonej usługi, użytkownik pobiera bieżącą wartość właściwości DBPROP_INIT_OLEDBSERVICES, ustawia lub czyści dla danej właściwości, które można włączać lub wyłączać i resetuje właściwości. DBPROP_INIT_OLEDBSERVICES można ustawić bezpośrednio w OLE DB lub w parametrach połączenia przekazano do ADO lub `IDataInitialize::GetDatasource`. Odpowiednie wartości, aby włączyć/wyłączyć poszczególne usługi są wymienione w poniższej tabeli.

|Włączone usługi domyślne|Wartość właściwości DBPROP_INIT_OLEDBSERVICES|Wartość w parametrach połączenia|
|------------------------------|------------------------------------------------|--------------------------------|
|Wszystkie usługi (ustawienie domyślne)|DBPROPVAL_OS_ENABLEALL|"Usług OLE DB = -1;"|
|Wszystkie regiony z wyjątkiem puli i AutoEnlistment|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"Usług OLE DB = -4;"|
|Wszystkie regiony z wyjątkiem kursor kliencki|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"Usług OLE DB = -5;"|
|Wszystkie z wyjątkiem buforowanie AutoEnlistment i kursor kliencki|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"Usług OLE DB = -7;"|
|Brak usług|`~DBPROPVAL_OS_ENABLEALL`|"Usług OLE DB = 0;"|

Jeśli wpis rejestru nie istnieje dla dostawcy, menedżerów składników nie są zbierane obiektów dostawcy. Brak usług zostanie włączona, nawet wtedy, gdy wyraźnie żąda przez użytkownika.

## <a name="see-also"></a>Zobacz też

[Korzystanie z puli zasobów](/previous-versions/windows/desktop/ms713655)<br/>
[Jaki sposób użytkownicy korzystają w puli zasobów](/previous-versions/windows/desktop/ms715907)<br/>
[Jak dostawców wydajnie pracować z puli zasobów](/previous-versions/windows/desktop/ms714906)<br/>
[Włączanie i wyłączanie usług OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>