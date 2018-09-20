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
ms.openlocfilehash: fbdf882367deb34570dd5b5ebb1b4001be739297
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373860"
---
# <a name="configure-visual-c-for-arm-processors"></a>Konfigurowanie Visual C++ dla procesorów ARM

Ten rozdział dokumentacji zawiera informacje o sposobie używania narzędzi kompilacji Visual C++ pod kątem sprzętu ARM.

## <a name="in-this-section"></a>W tej sekcji

[Przegląd konwencji ABI ARM](../build/overview-of-arm-abi-conventions.md)<br/>
W tym artykule opisano interfejsem binarnym aplikacji używane przez Windows na ARM, rejestrowanie użycia, Konwencje wywoływania oraz obsługi wyjątków.

[Przegląd konwencji ABI ARM64](../build/arm64-windows-abi-conventions.md)<br/>
W tym artykule opisano interfejsem binarnym aplikacji używane przez Windows dla procesorów ARM64 rejestrowanie użycia, Konwencje wywoływania oraz obsługi wyjątków.

[Typowe problemy przy migracji Visual C++ ARM](../build/common-visual-cpp-arm-migration-issues.md)<br/>
Opisuje elementy kodu C++, które są przyjmowane powszechnie jako przenośne w ramach architektury, ale które mogą wygenerować różne wyniki dla ARM niż dla x86 i x64.

[Obsługa wyjątków ARM](../build/arm-exception-handling.md)<br/>
W tym artykule opisano schemat kodowania dla odwijanie podczas obsługi w Windows na ARM wyjątków strukturalnych stosu.

[Obsługa wyjątków ARM64](../build/arm64-exception-handling.md)<br/>
W tym artykule opisano schemat kodowania dla odwijanie podczas obsługi wyjątków strukturalnych w Windows dla procesorów ARM64 stosu.

## <a name="related-sections"></a>Sekcje pokrewne

[Funkcje wewnętrzne ARM](../intrinsics/arm-intrinsics.md)<br/>
W tym artykule opisano funkcje wewnętrzne kompilatora dla procesorów korzystających z architektury ARM.
