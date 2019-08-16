---
title: 'Instrukcje: Tworzenie izolowanych aplikacji do korzystania ze składników COM'
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 8ae3c51502267f202cbb85ea7be2a81dc3310410
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493234"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Instrukcje: Tworzenie izolowanych aplikacji do korzystania ze składników COM

Aplikacje izolowane to aplikacje, które mają wbudowane manifesty w programie. Można tworzyć izolowane aplikacje do korzystania ze składników COM.

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Aby dodać odwołania COM do manifestów izolowanych aplikacji

1. Otwórz strony właściwości projektu dla aplikacji izolowanej.

1. Rozwiń węzeł **Właściwości konfiguracji** , a następnie rozwiń węzeł **narzędzie manifestu** .

1. Wybierz stronę właściwości **izolowany model com** , a następnie ustaw właściwość **Nazwa pliku składnika** na nazwę składnika com, który ma być wykorzystywany przez izolowaną aplikację.

1. Kliknij przycisk **OK**.

### <a name="to-build-manifests-into-isolated-applications"></a>Aby utworzyć manifesty w aplikacjach izolowanych

1. Otwórz strony właściwości projektu dla aplikacji izolowanej.

1. Rozwiń węzeł **Właściwości konfiguracji** , a następnie rozwiń węzeł **narzędzie manifestu** .

1. Wybierz stronę właściwości **dane wejściowe i wyjściowe** , a następnie ustaw właściwość **Osadź manifest** równą **tak**.

1. Kliknij przycisk **OK**.

1. Skompiluj rozwiązanie.

## <a name="see-also"></a>Zobacz także

[Aplikacje izolowane](/windows/win32/SbsCs/isolated-applications)<br/>
[Informacje o zestawach równoległych](/windows/win32/SbsCs/about-side-by-side-assemblies-)
