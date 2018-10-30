---
title: Interfejsy obiektu sesji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cf6f84791e0330c09f61ee612069564781086cc4
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216347"
---
# <a name="session-object-interfaces"></a>Interfejsy obiektu sesji

W poniższej tabeli przedstawiono interfejsów obowiązkowych i opcjonalnych, zdefiniowane przez OLE DB dla obiektu sesji.

|Interface|Wymagany?|Implementowany przez Szablony OLE DB?|
|---------------|---------------|--------------------------------------|
|[IGetDataSource](/previous-versions/windows/desktop/ms709721)|Obowiązkowy|Tak|
|[IOpenRowset](/previous-versions/windows/desktop/ms716946)|Obowiązkowy|Tak|
|[ISessionProperties](/previous-versions/windows/desktop/ms713721)|Obowiązkowy|Tak|
|[IAlterIndex](/previous-versions/windows/desktop/ms714943)|Optional|Nie|
|[IAlterTable](/previous-versions/windows/desktop/ms719764)|Optional|Nie|
|[IBindResource](/previous-versions/windows/desktop/ms714936)|Optional|Nie|
|[ICreateRow](/previous-versions/windows/desktop/ms716832)|Optional|Nie|
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625)|Optional|Tak|
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)|Optional|Tak|
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593)|Optional|Nie|
|[Interfejs ISupportErrorInfo](/previous-versions/windows/desktop/ms715816)|Optional|Tak|
|[ITableCreation](/previous-versions/windows/desktop/ms713639)|Optional|Nie|
|[ITableDefinition](/previous-versions/windows/desktop/ms714277)|Optional|Nie|
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947)|Optional|Nie|
|[Metody ITransaction](/previous-versions/windows/desktop/ms723053)|Optional|Nie|
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071)|Optional|Nie|
|[ITransactonLocal](/previous-versions/windows/desktop/ms714893)|Optional|Nie|
|[ITransactionObject](/previous-versions/windows/desktop/ms713659)|Optional|Nie|

Obiekt sesji tworzy się obiektu zestawu wierszy. Jeśli dostawca obsługuje poleceń, sesja wzrasta, powstaje obiekt polecenia (`CCommand`, implementowanie OLE DB `TCommand`). Obiekt polecenia implementuje `ICommand` interfejsu i używa `ICommand::Execute` metody do wykonywania poleceń w zestawie wierszy, jak pokazano na poniższej ilustracji.

![Diagram koncepcyjny dostawcy](../../data/oledb/media/vc4u551.gif "vc4u551")

## <a name="see-also"></a>Zobacz też

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
