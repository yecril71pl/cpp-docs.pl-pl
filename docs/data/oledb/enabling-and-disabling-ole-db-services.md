---
title: Włączanie i wyłączanie usług OLE DB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 72c890b94d84d170bb3ee01bd02d08fc00f9aa04
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068229"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Włączanie i wyłączanie usług OLE DB

Menedżer składników usługi OLE DB porównuje właściwości określone przez konsumentów do tych obsługiwanych przez dostawcę, aby ustalić, czy składniki poszczególne usługi można wywoływane w celu spełnienia rozszerzone funkcje wymagane przez klienta. Na przykład jeśli aplikacja żąda przewijany kursora i dostawca obsługuje jedynie kursora tylko do przodu, usługi Menedżer składników wywołuje składnik usługi Aparat kursora klienta, aby zapewnić funkcjonalność przewijany. Jeśli aplikacja powołuje się na rozszerzone funkcje obsługiwane domyślnie na dostawcy wierszy, a aplikacja wykonuje nie zostały jawnie ustaw właściwości, aby zażądać, że funkcje, funkcje mogą nie być wyświetlane na zestaw wierszy zwrócony przez klienta Aparat kursora. Jako międzyoperacyjnych, aplikacje powinny zawsze Ustaw właściwości w celu jawnego żądania rozszerzoną funkcjonalność w razie potrzeby.

W niektórych przypadkach może być konieczne wyłączenie poszczególnych usług OLE DB współdziała dobrze z istniejących aplikacji, które zakładają właściwości dostawcy. Usługi OLE DB zapewniają możliwość wyłączenia poszczególnych usług lub wszystkich usług, na podstawie połączenia przez połączenie lub dla wszystkich aplikacji za pomocą jednego dostawcy.

## <a name="see-also"></a>Zobacz też

[Buforowanie zasobów i usługi OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)