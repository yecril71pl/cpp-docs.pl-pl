---
title: Interfejsy obiektu sesji
ms.date: 10/24/2018
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
ms.openlocfilehash: 6b4748b804572c72b75f63b8ea2473818bdac989
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556624"
---
# <a name="session-object-interfaces"></a>Interfejsy obiektu sesji

W poniższej tabeli przedstawiono interfejsów obowiązkowych i opcjonalnych, zdefiniowane przez OLE DB dla obiektu sesji.

|Interface|Wymagany?|Implementowany przez Szablony OLE DB?|
|---------------|---------------|--------------------------------------|
|[IGetDataSource](https://docs.microsoft.com/previous-versions/windows/desktop/ms709721(v=vs.85))|Obowiązkowy|Tak|
|[IOpenRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms716946(v=vs.85))|Obowiązkowy|Tak|
|[ISessionProperties](https://docs.microsoft.com/previous-versions/windows/desktop/ms713721(v=vs.85))|Obowiązkowy|Tak|
|[IAlterIndex](https://docs.microsoft.com/previous-versions/windows/desktop/ms714943(v=vs.85))|Optional|Nie|
|[IAlterTable](https://docs.microsoft.com/previous-versions/windows/desktop/ms719764(v=vs.85))|Optional|Nie|
|[IBindResource](https://docs.microsoft.com/previous-versions/windows/desktop/ms714936(v=vs.85))|Optional|Nie|
|[ICreateRow](https://docs.microsoft.com/previous-versions/windows/desktop/ms716832(v=vs.85))|Optional|Nie|
|[IDBCreateCommand](https://docs.microsoft.com/previous-versions/windows/desktop/ms711625(v=vs.85))|Optional|Tak|
|[IDBSchemaRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms713686(v=vs.85))|Optional|Tak|
|[IIndexDefinition](https://docs.microsoft.com/previous-versions/windows/desktop/ms711593(v=vs.85))|Optional|Nie|
|[Interfejs ISupportErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/ms715816(v=vs.85))|Optional|Tak|
|[ITableCreation](https://docs.microsoft.com/previous-versions/windows/desktop/ms713639(v=vs.85))|Optional|Nie|
|[ITableDefinition](https://docs.microsoft.com/previous-versions/windows/desktop/ms714277(v=vs.85))|Optional|Nie|
|[ITableDefinitionWithConstraints](https://docs.microsoft.com/previous-versions/windows/desktop/ms720947(v=vs.85))|Optional|Nie|
|[Metody ITransaction](https://docs.microsoft.com/previous-versions/windows/desktop/ms723053(v=vs.85))|Optional|Nie|
|[ITransactionJoin](https://docs.microsoft.com/previous-versions/windows/desktop/ms718071(v=vs.85))|Optional|Nie|
|[ITransactonLocal](https://docs.microsoft.com/previous-versions/windows/desktop/ms714893(v=vs.85))|Optional|Nie|
|[ITransactionObject](https://docs.microsoft.com/previous-versions/windows/desktop/ms713659(v=vs.85))|Optional|Nie|

Obiekt sesji tworzy się obiektu zestawu wierszy. Jeśli dostawca obsługuje poleceń, sesja wzrasta, powstaje obiekt polecenia (`CCommand`, implementowanie OLE DB `TCommand`). Obiekt polecenia implementuje `ICommand` interfejsu i używa `ICommand::Execute` metody do wykonywania poleceń w zestawie wierszy, jak pokazano na poniższej ilustracji.

![Diagram koncepcyjny dostawcy](../../data/oledb/media/vc4u551.gif "vc4u551")

## <a name="see-also"></a>Zobacz też

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
