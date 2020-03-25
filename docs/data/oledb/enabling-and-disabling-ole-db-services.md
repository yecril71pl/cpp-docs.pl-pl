---
title: Włączanie i wyłączanie usług OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: 3016126d09b39ec74f4acb758a2176be05052648
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210967"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Włączanie i wyłączanie usług OLE DB

Menedżer składników usługi OLE DB porównuje właściwości określone przez konsumenta z właściwościami obsługiwanymi przez dostawcę w celu określenia, czy poszczególne składniki usługi mogą być używane do zaspokojenia rozszerzonych funkcji zażądanych przez klienta. Na przykład jeśli aplikacja żąda przewijanego kursora, a dostawca obsługuje tylko kursor tylko do przodu, Menedżer składników usług używa składnika usługi aparat kursora klienta w celu zapewnienia możliwości przewijania. Jeśli aplikacja korzysta z rozszerzonych funkcji obsługiwanych domyślnie w zestawie wierszy dostawcy, a aplikacja nie ustawi jawnie właściwości do żądania tej funkcjonalności, funkcjonalność może nie być widoczna w zestawie wierszy zwracanym przez klienta. Aparat kursora. Aby można było współdziałać, aplikacje powinny zawsze ustawiać właściwości, aby jawnie zażądać rozszerzonych funkcji, gdy jest to konieczne.

W niektórych przypadkach może być konieczne wyłączenie poszczególnych usług OLE DB, aby działały prawidłowo z istniejącymi aplikacjami, które składają się na informacje o charakterystyce dostawcy. Usługi OLE DB umożliwiają wyłączenie poszczególnych usług lub wszystkich usług, w zależności od połączenia lub dla wszystkich aplikacji korzystających z jednego dostawcy.

## <a name="see-also"></a>Zobacz też

[Buforowanie zasobów i usługi OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)
