---
title: Kompilowanie izolowanych kompilacji C/C++
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: 42192ad9388a8e69b70947c20c6fa7ee428a2bb9
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220958"
---
# <a name="building-cc-isolated-applications"></a>Kompilowanie izolowanych kompilacji C/C++

Aplikacja izolowana zależy tylko od zestawów side-by-side i tworzy powiązanie z jego zależności za pomocą manifestu. Nie jest wymagane dla badanej aplikacji to całkowicie odizolowane, aby można było poprawnie uruchomić na Windows; jednak zainwestować w tworzenie aplikacji w pełni izolowane, użytkownik może zaoszczędzić czas Jeśli potrzebujesz do obsługi aplikacji w przyszłości. Aby uzyskać więcej informacji o zaletach tworzenie aplikacji w pełni izolowane, zobacz [aplikacje izolowane](/windows/desktop/SbsCs/isolated-applications).

Podczas kompilowania z natywnego języka C /C++ aplikacji przy użyciu programu Visual Studio domyślnie system projektu programu Visual Studio generuje plik manifestu, który opisuje zależności aplikacji w bibliotekach programu Visual Studio. Jeśli są one tylko zależności Twoja aplikacja ma, a następnie staje się izolowanych aplikacji tak szybko, jak zostanie odtworzony z programem Visual Studio. Jeśli Twoja aplikacja używa innych bibliotek w czasie wykonywania, a następnie może być konieczne odbudowanie tych bibliotek jako zestawów side-by-side wykonując kroki opisane w [zestawy języka C/C++ — równoczesne tworzenie](building-c-cpp-side-by-side-assemblies.md).

## <a name="see-also"></a>Zobacz także

[Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
