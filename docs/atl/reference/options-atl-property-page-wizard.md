---
title: Opcje, Kreator strony właściwości ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: c883b3e79bd857bb457da0a1bd540a08ddddf017
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524543"
---
# <a name="options-atl-property-page-wizard"></a>Opcje, Kreator strony właściwości ATL


::: moniker range="vs-2019"

Kreator strony właściwości ATL nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

::: moniker-end

::: moniker range="vs-2017"

Ta strona kreatora umożliwia definiowanie wątkowości modelu i agregację poziomu strony właściwości, które tworzysz.

- **Model wątkowości**

   Określa model wątkowy posługują się na stronie właściwości.

   Zobacz [określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) Aby uzyskać więcej informacji.

   |Opcja|Opis|
   |------------|-----------------|
   |**Single**|Na stronie właściwości działa tylko w podstawowym wątku com.|
   |**Apartamentu**|Na stronie właściwości można utworzyć w dowolnym komórka wątku pojedynczego. Domyślnie.|

- **Agregacja**

   Dodaje obsługę agregacji dla strony właściwości, które tworzysz. Zobacz [agregacji](../../atl/aggregation.md) Aby uzyskać więcej informacji.

   |Opcja|Opis|
   |------------|-----------------|
   |**Tak**|Utwórz stronę właściwości, który może być agregowany.|
   |**Brak**|Utwórz stronę właściwości nie można agregować.|
   |**Only**|Utwórz stronę właściwości wystąpienia można tworzyć tylko za pomocą agregacji.|

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Kreator strony właściwości ATL](../../atl/reference/atl-property-page-wizard.md)<br/>
[Ciągi, Kreator strony właściwości ATL](../../atl/reference/strings-atl-property-page-wizard.md)
