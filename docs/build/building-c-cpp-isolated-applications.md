---
title: Kompilowanie izolowanych kompilacji C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: 6ff9ada45a1ddd7c0aa1da62f6dd7f6a7b7bf371
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534930"
---
# <a name="building-cc-isolated-applications"></a>Kompilowanie izolowanych kompilacji C/C++

Aplikacja izolowana zależy tylko od zestawów side-by-side i tworzy powiązanie z jego zależności za pomocą manifestu. Nie jest wymagane dla badanej aplikacji to całkowicie odizolowane, aby można było poprawnie uruchomić na Windows; jednak zainwestować w tworzenie aplikacji w pełni izolowane, użytkownik może zaoszczędzić czas Jeśli potrzebujesz do obsługi aplikacji w przyszłości. Aby uzyskać więcej informacji o zaletach tworzenie aplikacji w pełni izolowane, zobacz [aplikacje izolowane](/windows/desktop/SbsCs/isolated-applications).

W przypadku tworzenia natywnych aplikacji C/C++ za pomocą języka Visual C++, system projektu domyślnie programu Visual Studio generuje plik manifestu, opisująca zależności aplikacji na bibliotek języka Visual C++. Jeśli są one tylko zależności Twoja aplikacja ma, a następnie staje się izolowanych aplikacji tak szybko, jak zostanie odtworzony z programem Visual Studio. Jeśli Twoja aplikacja używa innych bibliotek w czasie wykonywania, a następnie może być konieczne odbudowanie tych bibliotek jako zestawów side-by-side wykonując kroki opisane w [zestawy języka C/C++ — równoczesne tworzenie](../build/building-c-cpp-side-by-side-assemblies.md).

## <a name="see-also"></a>Zobacz też

[Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)