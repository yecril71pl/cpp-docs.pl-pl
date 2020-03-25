---
title: Testowanie dostawcy
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: b1f068c928abd0a6656bed0702422d9bda843208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209508"
---
# <a name="testing-your-provider"></a>Testowanie dostawcy

Przed zwolnieniem dostawcy należy wykonać następujące testy w podanej kolejności. Te testy pokazują, że dostawca działa prawidłowo dla większości potencjalnych użytkowników.

1. Przetestuj dostawcę przy użyciu aplikacji [konsumenckiej](../../data/oledb/creating-an-ole-db-consumer.md) zapisaną przy użyciu szablonów konsumentów OLE DB. Konsument testowy powinien obejmować wszystkie obszary funkcjonalne dostawcy (cały kod, który został dodany lub zmodyfikowany).

1. Przetestuj dostawcę przy użyciu aplikacji konsumenta zapisaną przy użyciu modelu ADO. Większość deweloperów (zwłaszcza Microsoft Visual Basic i Microsoft C# Developers) korzysta z obiektów ADO lub ADO.NET dla aplikacji konsumenckich. Konsument testowy powinien obejmować wszystkie obszary funkcjonalne dostawcy. Przykład aplikacji konsumenckiej ADO zawiera [przykłady kodu ADO w programie Microsoft Visual Basic](/previous-versions/ms807514(v=msdn.10)).

1. Uruchom testy zgodności OLE DB (w tym testy zgodne z ADO), aby pokazać, że Twój dostawca spełnia normy poziomu 0 dla dostawców OLE DB. (Aby uzyskać wyjaśnienie poziomu 0, Wyszukaj **testy zgodne z poziomem OLE DB 0** w [przewodniku OLE DB programisty](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Te testy i powiązane dokumenty są dołączone do wizualizacji C++ w zestawie SDK dostępu do danych. Te testy pomagają również sprawdzić, czy dostawca działa dobrze, gdy są agregowane przez innych [dostawców usług](../../data/oledb/ole-db-resource-pooling-and-services.md) i są szczególnie przydatne w przypadku modyfikowania lub dodawania właściwości. Aby uzyskać więcej informacji na temat testów zgodności, zobacz plik Readme dla zestawu SDK dostępu do danych, który znajduje się na jednym z dysków CD programu Visual Studio.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
