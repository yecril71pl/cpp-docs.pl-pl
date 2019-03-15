---
title: Konfigurowanie projektów w języku C++ dla procesorów ARM
ms.date: 07/11/2018
ms.assetid: 3d95f221-656a-480d-9651-9ad263895747
ms.openlocfilehash: 7e6e0c97245c0941abc49096d1693a8d152c1709
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812476"
---
# <a name="configure-c-projects-for-arm-processors"></a>Konfigurowanie projektów w języku C++ dla procesorów ARM

Ten rozdział dokumentacji zawiera informacje o sposobie używania narzędzia do kompilacji MSVC pod kątem sprzętu ARM.

## <a name="in-this-section"></a>W tej sekcji

[Przegląd konwencji ABI ARM](overview-of-arm-abi-conventions.md)<br/>
W tym artykule opisano interfejsem binarnym aplikacji używane przez Windows na ARM, rejestrowanie użycia, Konwencje wywoływania oraz obsługi wyjątków.

[Przegląd konwencji ABI ARM64](arm64-windows-abi-conventions.md)<br/>
W tym artykule opisano interfejsem binarnym aplikacji używane przez Windows dla procesorów ARM64 rejestrowanie użycia, Konwencje wywoływania oraz obsługi wyjątków.

[Typowe problemy przy migracji ARM MSVC](common-visual-cpp-arm-migration-issues.md)<br/>
Opisuje elementy kodu C++, które są przyjmowane powszechnie jako przenośne w ramach architektury, ale które mogą wygenerować różne wyniki dla ARM niż dla x86 i x64.

[Obsługa wyjątków ARM](arm-exception-handling.md)<br/>
W tym artykule opisano schemat kodowania dla odwijanie podczas obsługi w Windows na ARM wyjątków strukturalnych stosu.

[Obsługa wyjątków ARM64](arm64-exception-handling.md)<br/>
W tym artykule opisano schemat kodowania dla odwijanie podczas obsługi wyjątków strukturalnych w Windows dla procesorów ARM64 stosu.

## <a name="related-sections"></a>Sekcje pokrewne

[Funkcje wewnętrzne ARM](../intrinsics/arm-intrinsics.md)<br/>
W tym artykule opisano funkcje wewnętrzne kompilatora dla procesorów korzystających z architektury ARM.
