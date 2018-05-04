---
title: Konfigurowanie programu Visual C++ dla procesorów ARM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3d95f221-656a-480d-9651-9ad263895747
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b249e2b54085f87c4895ba026d4f34e9ed195a49
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="configure-visual-c-for-arm-processors"></a>Konfigurowanie programu Visual C++ dla procesorów ARM

Ta sekcja dokumentacji zawiera informacje o sposobie korzystania z narzędzi kompilacji Visual C++ pod kątem sprzętu ARM.  
  
## <a name="in-this-section"></a>W tej sekcji  

[Przegląd konwencji ABI ARM](../build/overview-of-arm-abi-conventions.md)  
Opisuje interfejs binarne aplikacji używane przez system Windows na ARM dla rejestrowania użycia, Konwencje wywoływania oraz obsługi wyjątków.  
  
[Typowe problemy przy migracji Visual C++ ARM](../build/common-visual-cpp-arm-migration-issues.md)  
W tym artykule opisano elementy kodu C++, które są często zakłada się, że można przenośnych w ramach architektury, ale które wygenerować różne wyniki dla ARM niż dla x86 i x64.  
  
[Obsługa wyjątków ARM](../build/arm-exception-handling.md)  
W tym artykule opisano schemat kodowania stosu rozwinięcia podczas obsługi w systemie Windows na ARM wyjątków strukturalnych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
[Funkcje wewnętrzne ARM](../intrinsics/arm-intrinsics.md)  
Opisuje funkcje wewnętrzne kompilatora procesorów, korzystających z architektury ARM.