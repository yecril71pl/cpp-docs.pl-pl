---
title: Interfejsy obiektu sesji
ms.date: 11/19/2018
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
ms.openlocfilehash: 2fb91365fec0709e1bb2a26afa519e6565862681
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031459"
---
# <a name="session-object-interfaces"></a>Interfejsy obiektu sesji

W poniższej tabeli przedstawiono interfejsów obowiązkowych i opcjonalnych, zdefiniowane przez OLE DB dla obiektu sesji.

|Interface|Wymagany?|Implementowany przez Szablony OLE DB?|
|---------------|---------------|--------------------------------------|
|[IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85))|Obowiązkowy|Tak|
|[IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85))|Obowiązkowy|Yes|
|[ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85))|Obowiązkowy|Tak|
|[IAlterIndex](/previous-versions/windows/desktop/ms714943(v=vs.85))|Optional|Nie|
|[IAlterTable](/previous-versions/windows/desktop/ms719764(v=vs.85))|Optional|Nie|
|[IBindResource](/previous-versions/windows/desktop/ms714936(v=vs.85))|Optional|Nie|
|[ICreateRow](/previous-versions/windows/desktop/ms716832(v=vs.85))|Optional|Nie|
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85))|Optional|Tak|
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))|Optional|Tak|
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593(v=vs.85))|Optional|Nie|
|[Interfejs ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Optional|Tak|
|[ITableCreation](/previous-versions/windows/desktop/ms713639(v=vs.85))|Optional|Nie|
|[ITableDefinition](/previous-versions/windows/desktop/ms714277(v=vs.85))|Optional|Nie|
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947(v=vs.85))|Optional|Nie|
|[Metody ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|Optional|Nie|
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071(v=vs.85))|Optional|Nie|
|[ITransactonLocal](/previous-versions/windows/desktop/ms714893(v=vs.85))|Optional|Nie|
|[ITransactionObject](/previous-versions/windows/desktop/ms713659(v=vs.85))|Optional|Nie|

Obiekt sesji tworzy się obiektu zestawu wierszy. Jeśli dostawca obsługuje poleceń, sesja wzrasta, powstaje obiekt polecenia (`CCommand`, implementowanie OLE DB `TCommand`). Obiekt polecenia implementuje `ICommand` interfejsu i używa `ICommand::Execute` metody do wykonywania poleceń w zestawie wierszy, jak pokazano na poniższej ilustracji.

![Diagram koncepcyjny dostawcy](../../data/oledb/media/vc4u551.gif "diagram pojęciowy dostawcy")

## <a name="see-also"></a>Zobacz także

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
