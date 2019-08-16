---
title: Ogólne informacje o tworzeniu manifestu dla programów C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: 16d5efc5c5f7ce81b4b60269b0c666fd5d24266e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492525"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Ogólne informacje o tworzeniu manifestu dla programów C/C++

[Manifest](/windows/win32/sbscs/manifests) to dokument XML, który może być zewnętrznym plikiem XML lub zasobem osadzonym wewnątrz aplikacji lub zestawu. Manifest [izolowanej aplikacji](/windows/win32/SbsCs/isolated-applications) służy do zarządzania nazwami i wersjami wspólnych zestawów równoległych, do których aplikacja powinna powiązać w czasie wykonywania. Manifest zestawu równoległego określa jego zależności od nazw, wersji, zasobów i innych zestawów.

Istnieją dwa sposoby tworzenia manifestu dla izolowanej aplikacji lub zestawu side-by-side. Po pierwsze autor zestawu może ręcznie utworzyć plik manifestu, wykonując reguły i wymagania dotyczące nazewnictwa. Alternatywnie, jeśli program zależy tylko od zestawów wizualizacji C++ , takich jak CRT, MFC, ATL lub innych, można automatycznie wygenerować manifest przez konsolidator.

Nagłówki bibliotek wizualnych C++ zawierają informacje o zestawie i gdy biblioteki są zawarte w kodzie aplikacji, to informacje o zestawie są używane przez konsolidatora do tworzenia manifestu dla końcowego pliku binarnego. Konsolidator nie osadza pliku manifestu wewnątrz danych binarnych i może generować tylko manifest jako plik zewnętrzny. Posiadanie manifestu jako pliku zewnętrznego może nie zadziałało dla wszystkich scenariuszy. Na przykład zaleca się, aby zestawy prywatne miały osadzone manifesty. W przypadku kompilacji wiersza polecenia, takich jak te, które używają NMAKE do kompilowania kodu, manifest może być osadzony przy użyciu narzędzia manifestu; Aby uzyskać więcej informacji, zobacz [generowanie manifestu w wierszu polecenia](manifest-generation-at-the-command-line.md). Podczas kompilowania w programie Visual Studio manifest może być osadzony przez ustawienie właściwości narzędzia manifestu w oknie dialogowym **właściwości projektu** ; Zobacz [generowanie manifestu w programie Visual Studio](manifest-generation-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także

[Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
