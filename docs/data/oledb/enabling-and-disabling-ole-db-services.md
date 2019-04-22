---
title: Włączanie i wyłączanie usług OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: df17a55950b03d4d63dea2199e3bc19bedb8a7e3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028957"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Włączanie i wyłączanie usług OLE DB

Menedżer składników usługi OLE DB porównuje właściwości określone przez konsumenta właściwości obsługiwanych przez dostawcę, aby ustalić, czy składniki usługi poszczególnych może służyć do spełnienia rozszerzone funkcje wymagane przez klienta. Na przykład jeśli aplikacja żąda przewijany kursora i dostawca obsługuje jedynie kursora tylko do przodu, usługi Menedżer składników używa składnika usługi Aparat kursora klienta do zapewnienia przewijany funkcji. Jeśli aplikacja powołuje się na rozszerzone funkcje obsługiwane domyślnie na dostawcy wierszy, a aplikacja nie jawnie ustawić właściwości żądania, że funkcje, funkcje mogą nie być wyświetlane na zestaw wierszy zwrócony przez klienta Aparat kursora. Jako międzyoperacyjnych, aplikacje powinny zawsze Ustaw właściwości w celu jawnego żądania rozszerzoną funkcjonalność w razie potrzeby.

W niektórych przypadkach może być konieczne wyłączenie poszczególnych usług OLE DB współdziała dobrze z istniejących aplikacji, które zakładają właściwości dostawcy. Usługi OLE DB zapewniają możliwość wyłączenia poszczególnych usług lub wszystkich usług, na podstawie połączenia przez połączenie lub dla wszystkich aplikacji za pomocą jednego dostawcy.

## <a name="see-also"></a>Zobacz także

[Buforowanie zasobów i usługi OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)