---
title: Kompilowanie izolowanych kompilacji C/C++
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: fbb553e3514ac3c32ee1e1f276dcb3e43d3a192e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493344"
---
# <a name="building-cc-isolated-applications"></a>Kompilowanie izolowanych kompilacji C/C++

Izolowana aplikacja zależy tylko od zestawów równoległych i wiąże się z jej zależnościami przy użyciu manifestu. Nie jest wymagane, aby aplikacja była całkowicie izolowana w celu prawidłowego działania w systemie Windows; Jednak dzięki zainwestowaniu w aplikację w sposób całkowicie odizolowany, można zaoszczędzić czas, jeśli trzeba będzie obniżyć swoją aplikację w przyszłości. Aby uzyskać więcej informacji na temat zalet tworzenia aplikacji w sposób całkowicie izolowany, zobacz [izolowane aplikacje](/windows/win32/SbsCs/isolated-applications).

Podczas kompilowania natywnej aplikacji CC++ /w programie Visual Studio domyślnie system projektu programu Visual Studio generuje plik manifestu, który opisuje zależności aplikacji w bibliotekach programu Visual Studio. Jeśli są to jedyne zależności aplikacji, to zostanie ona izolowana, gdy tylko zostanie odbudowana przy użyciu programu Visual Studio. Jeśli aplikacja korzysta z innych bibliotek w czasie wykonywania, może być konieczne odbudowanie tych bibliotek jako zestawów równoległych zgodnie z krokami opisanymi w temacie Tworzenie zestawów wykonywanych w języku [C/C++ Side-Side](building-c-cpp-side-by-side-assemblies.md).

## <a name="see-also"></a>Zobacz także

[Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
