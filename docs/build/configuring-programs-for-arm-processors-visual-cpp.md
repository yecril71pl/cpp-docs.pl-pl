---
title: Konfigurowanie Visual C++ dla procesorów ARM
ms.date: 07/11/2018
ms.assetid: 3d95f221-656a-480d-9651-9ad263895747
ms.openlocfilehash: 9238bf9342984e788d3abe6d7da8b0974a78ac24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594223"
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
