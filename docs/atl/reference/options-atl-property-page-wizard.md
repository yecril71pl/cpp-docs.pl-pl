---
title: Opcje, Kreator strony właściwości ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.ppg.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92f3855cf9c760ef8e6bb761f4a0bac042f8c539
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081770"
---
# <a name="options-atl-property-page-wizard"></a>Opcje, Kreator strony właściwości ATL

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

## <a name="see-also"></a>Zobacz też

[Kreator strony właściwości ATL](../../atl/reference/atl-property-page-wizard.md)<br/>
[Ciągi, Kreator strony właściwości ATL](../../atl/reference/strings-atl-property-page-wizard.md)

