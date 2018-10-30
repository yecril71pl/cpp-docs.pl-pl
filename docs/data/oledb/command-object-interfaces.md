---
title: Interfejsy obiektu polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f5d09e5794b66895d4bfd6a12fe7b0e1dbeeea7f
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216334"
---
# <a name="command-object-interfaces"></a>Interfejsy obiektu polecenia

Obiekt polecenia używa `IAccessor` interfejsu w celu określenia powiązania parametrów. Wywołania konsumenta `IAccessor::CreateAccessor`, przekazanie do niej tablicę `DBBINDING` struktury. `DBBINDING` zawiera informacje dotyczące powiązania kolumny (takie jak typ i długość). Dostawca otrzymuje struktur i określa, jak należy przenieść dane i czy konwersje są niezbędne.

`ICommandText` Interfejs zapewnia sposób, aby określić polecenie tekstu. `ICommandProperties` Interfejs obsługuje wszystkie właściwości polecenia.

## <a name="see-also"></a>Zobacz też

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
