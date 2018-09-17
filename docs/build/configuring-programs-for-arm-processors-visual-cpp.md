---
title: Konfigurowanie Visual C++ dla procesorów ARM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/11/2018
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
ms.openlocfilehash: 3ce0e7e1f7c0936daed0fa6a51f6e254403205e0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714964"
---
# <a name="configure-visual-c-for-arm-processors"></a>Konfigurowanie Visual C++ dla procesorów ARM

Ten rozdział dokumentacji zawiera informacje o sposobie używania narzędzi kompilacji Visual C++ pod kątem sprzętu ARM.

## <a name="in-this-section"></a>W tej sekcji

[Przegląd Konwencji ABI ARM](../build/overview-of-arm-abi-conventions.md) opisuje interfejsem binarnym aplikacji używane przez Windows na ARM, rejestrowanie użycia, Konwencje wywoływania oraz obsługi wyjątków.

[Przegląd Konwencji ABI ARM64](../build/arm64-windows-abi-conventions.md) opisuje interfejsem binarnym aplikacji używane przez Windows dla procesorów ARM64 rejestrowanie użycia, Konwencje wywoływania oraz obsługi wyjątków.

[Typowe Visual C++ ARM problemy przy migracji](../build/common-visual-cpp-arm-migration-issues.md) elementy kodu C++ w tym artykule opisano, które są przyjmowane powszechnie jako przenośne w ramach architektury, ale które mogą wygenerować różne wyniki dla ARM niż dla x86 i x64.

[Obsługa wyjątków ARM](../build/arm-exception-handling.md) opisano schemat kodowania dla odwijanie podczas obsługi w Windows na ARM wyjątków strukturalnych stosu.

[Obsługa wyjątków ARM64](../build/arm64-exception-handling.md) opisano schemat kodowania dla odwijanie podczas obsługi w Windows dla procesorów ARM64 wyjątków strukturalnych stosu.

## <a name="related-sections"></a>Sekcje pokrewne

[Funkcje wewnętrzne ARM](../intrinsics/arm-intrinsics.md) Opisuje funkcje wewnętrzne kompilatora dla procesorów korzystających z architektury ARM.
