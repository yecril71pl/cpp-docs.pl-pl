---
title: Unicode i MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], Unicode
- MFC [C++], character sets
- character sets [C++], multibyte
- run-time libraries [C++], language portability
- character sets [C++], Unicode
- Unicode [C++], MFC and C run-time functions
- multibyte characters [C++]
- runtime [C++], language portability
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
ms.openlocfilehash: 063c8b39ee0d29403b382b57a236f2a3e8759e3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375755"
---
# <a name="unicode-and-mbcs"></a>Unicode i MBCS

Biblioteka klas Microsoft Foundation (MFC), biblioteka w czasie wykonywania języka C dla języka Visual C++ i środowisko programistyczne Visual C++ są włączone do programowania międzynarodowego. Zapewniają one:

- Obsługa standardu Unicode w systemie Windows. Unicode jest aktualnym standardem i powinien być używany w miarę możliwości.

   Unicode to 16-bitowe kodowanie znaków, zapewniające wystarczającą ilość kodowania dla wszystkich języków. Wszystkie znaki ASCII są zawarte w Unicode jako znaki rozszerzone.

- Obsługa postaci zestawu znaków wielobajtowych (MBCS) o nazwie zestaw znaków dwubajtowych (DBCS) na wszystkich platformach.

   Znaki DBCS składają się z 1 lub 2 bajtów. Niektóre zakresy bajtów są odstawienia do użycia jako bajty potencjalnych potencjalnych. Bajt wiodący określa, że i następujący bajt szlaku składają się z pojedynczego znaku o szerokości 2 bajtów. Należy śledzić, które bajty są bajtami potencjalnych potencjalnych potencjalnych przewodów. W określonym zestawie znaków wielobajtowych bajty potencjalnego klienta mieszczą się w określonym zakresie, podobnie jak bajty szlaku. Gdy te zakresy nakładają się na siebie, może być konieczne dokonanie oceny kontekstu w celu ustalenia, czy dany bajt działa jako bajt wiodący lub bajt szlaku.

- Wsparcie dla narzędzi, które upraszczają programowanie MBCS aplikacji napisanych na rynki międzynarodowe.

   Po uruchomieniu w wersji systemu operacyjnego Windows z obsługą MBCS system programistyczny Visual C++ — w tym zintegrowany edytor kodu źródłowego, debuger i narzędzia wiersza polecenia — jest całkowicie włączony w tryb MBCS. Aby uzyskać więcej informacji, zobacz [obsługę MBCS w języku Visual C++](../text/mbcs-support-in-visual-cpp.md).

> [!NOTE]
> W tej dokumentacji MBCS jest używany do opisania wszystkich non-Unicode obsługi znaków wielobajtowych. W języku Visual C++MBCS zawsze oznacza DBCS. Zestawy znaków szersze niż 2 bajty nie są obsługiwane.

Z definicji zestaw znaków ASCII jest podzbiorem wszystkich zestawów znaków wielobajtowych. W wielu zestawach znaków wielobajtowych każdy znak w zakresie 0x00 - 0x7F jest identyczny ze znakiem, który ma taką samą wartość w zestawie znaków ASCII. Na przykład w ciągach znaków ASCII i MBCS znak NULL 1-bajtowy ('\0') ma wartość 0x00 i wskazuje kończący się znak null.

## <a name="see-also"></a>Zobacz też

[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)<br/>
[Włączanie internacjonalizacji](../text/international-enabling.md)
