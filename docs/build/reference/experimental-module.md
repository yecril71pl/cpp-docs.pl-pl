---
title: '/Experimental: moduł (Włącz obsługę modułów)'
description: 'Użyj opcji kompilatora/Experimental: module, aby włączyć eksperymentalną obsługę kompilatora dla modułów.'
ms.date: 09/03/2019
f1_keywords:
- module
- /experimental:module
helpviewer_keywords:
- module
- /experimental:module
- Enable module support
ms.openlocfilehash: 0eea5127f651eaff30c197271ae6da38ac1356be
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075728"
---
# <a name="experimentalmodule-enable-module-support"></a>/Experimental: moduł (Włącz obsługę modułów)

Włącza eksperymentalną obsługę kompilatora dla modułów, zgodnie z projektem standard C++ 20.

## <a name="syntax"></a>Składnia

> **/Experimental: moduł**[ **-** ]

## <a name="remarks"></a>Uwagi

Obsługę modułów eksperymentalnych można włączyć, korzystając z opcji kompilatora **/Experimental: module** oraz opcji [/std: c + + Najnowsza](std-specify-language-standard-version.md) . Możesz użyć **/Experimental: module-** , aby wyłączyć obsługę modułów jawnie.

Ta opcja jest dostępna począwszy od programu Visual Studio 2015 Update 1. Począwszy od programu Visual Studio 2019 w wersji 16,2, projekty języka standardowego C++ 20 nie są w pełni zaimplementowane w kompilatorze języka Microsoft C++. Za pomocą funkcji modułów można tworzyć moduły z jedną partycją i importować moduły biblioteki standardowej udostępniane przez firmę Microsoft. Moduł i kod, który go zużywa, muszą być kompilowane z tymi samymi opcjami kompilatora.

Aby uzyskać więcej informacji o modułach i sposobach ich użycia i tworzenia, zobacz [Omówienie modułów w języku C++](../../cpp/modules-cpp.md).

Poniżej przedstawiono przykład opcji wiersza polecenia kompilatora używanych do tworzenia modułu eksportu z pliku źródłowego *ModuleName. IXX*:

```cmd
cl /EHsc /MD /experimental:module /module:export /module:name ModuleName /module:wrapper C:\Output\path\ModuleName.h /module:output C:\Output\path\ModuleName.ifc -c ModuleName.ixx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Ustaw listę rozwijaną **konfiguracji** na **wszystkie konfiguracje**.

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja języka**C/C++**  >  **Language** .

1. Zmodyfikuj właściwość **enable C++ modules (eksperymentalne)** , a następnie wybierz przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[`/headerUnit` (Użyj IFC jednostki nagłówka)](headerunit.md)\
[`/module:exportHeader` (Utwórz jednostki nagłówka)](module-exportheader.md)\
[`/module:reference` (Użyj nazwanego modułu IFC)](module-reference.md)\
[`/translateInclude` (Przetłumacz dyrektywy include na dyrektywy import)](translateinclude.md)\
[/Zc (Zgodność)](zc-conformance.md)
