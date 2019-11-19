---
title: Konfigurowanie projektów języka C++ dla procesorów ARM
ms.date: 07/11/2018
ms.assetid: 3d95f221-656a-480d-9651-9ad263895747
ms.openlocfilehash: 0dc87e9a119f82c03a11dde0d90c27de71618f5a
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163427"
---
# <a name="configure-c-projects-for-arm-processors"></a>Konfigurowanie projektów języka C++ dla procesorów ARM

Ta sekcja dokumentacji zawiera informacje o sposobach używania narzędzi kompilacji MSVC do kierowania sprzętu ARM.

## <a name="in-this-section"></a>W tej sekcji

[Omówienie Konwencji ABI ARM](overview-of-arm-abi-conventions.md)\
Opisuje interfejs binarny aplikacji używany przez system Windows w usłudze ARM do rejestrowania użycia, konwencji wywoływania i obsługi wyjątków.

[Omówienie Konwencji arm64 ABI](arm64-windows-abi-conventions.md)\
Opisuje interfejs binarny aplikacji używany przez system Windows w systemie ARM64 do rejestrowania użycia, konwencji wywoływania i obsługi wyjątków.

[Typowe problemy z migracją w usłudze MSVC ARM](common-visual-cpp-arm-migration-issues.md)\
Opisuje C++ elementy kodu, które są powszechnie założono, że są przenośne między architekturami, ale które tworzą różne wyniki dla ARM niż w przypadku procesorów x86 i x64.

[Obsługa wyjątków ARM](arm-exception-handling.md)\
Opisuje schemat kodowania dla rozwinięcia stosu podczas strukturalnej obsługi wyjątków w systemie Windows na platformie ARM.

[Obsługa wyjątków ARM64](arm64-exception-handling.md)\
Opisuje schemat kodowania dla rozwinięcia stosu podczas obsługi wyjątków strukturalnych w systemie Windows na ARM64.

## <a name="related-sections"></a>Sekcje pokrewne

\ [wewnętrzne ARM](../intrinsics/arm-intrinsics.md)
Opisuje funkcje wewnętrzne kompilatora dla procesorów korzystających z architektury ARM.

[Arm64 wewnętrzne](../intrinsics/arm-intrinsics.md)\
Opisuje funkcje wewnętrzne kompilatora dla procesorów korzystających z architektury ARM64.
