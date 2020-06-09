---
title: Mapowanie komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], about message maps
- mappings [MFC], commands
- commands [MFC], mapping
- command mapping [MFC]
- message handling [MFC], connecting to handler functions
- commands [MFC], connecting to handler functions
- mappings [MFC], messages
- messages [MFC], mapping
ms.assetid: 996f0652-0698-4b8c-b893-cdaa836d9d0f
ms.openlocfilehash: 16d6d7725d82bed6c9bfc02e408b68dcf7ffe5e4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625492"
---
# <a name="mapping-messages"></a>Mapowanie komunikatów

Każda Klasa struktury, która może odbierać wiadomości lub polecenia, ma swoją własną "mapę wiadomości". Struktura używa map komunikatów do łączenia komunikatów i poleceń z ich funkcjami obsługi. Każda klasa pochodna klasy `CCmdTarget` może mieć mapę komunikatów. Inne artykuły objaśniają szczegółowo mapy komunikatów i opisują sposób ich używania.

W odniesieniu do nazwy "Mapa komunikatów" mapy komunikatów obsługują zarówno komunikaty, jak i polecenia — wszystkie trzy kategorie komunikatów wymienione w [kategorii komunikatów](message-categories.md).

## <a name="see-also"></a>Zobacz też

[Komunikaty i polecenia w strukturze](messages-and-commands-in-the-framework.md)
