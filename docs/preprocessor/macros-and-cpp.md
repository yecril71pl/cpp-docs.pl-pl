---
title: Makra i język C++
ms.date: 08/29/2019
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: 8a86fb81544af91d4e844fb08b7948a589976e04
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220799"
---
# <a name="macros-and-c"></a>Makra i język C++

C++oferuje nowe możliwości, z których niektóre supplantją te, które są oferowane przez preprocesor ANSI C. Te nowe funkcje rozszerzają bezpieczeństwo typów i przewidywalność języka:

- W C++programie obiekty zadeklarowane jako **const** mogą być używane w wyrażeniach stałych. Umożliwia to programom deklarowanie stałych, które mają informacje o typie i wartości. Mogą deklarować wyliczenia, które mogą być wyświetlane symbolicznie z debugerem. W przypadku używania `#define` dyrektywy preprocesora do definiowania stałych nie jest to dokładne i nie jest bezpieczna pod względem typów. Nie przydzielono żadnego magazynu dla obiektu **const** , chyba że program zawiera wyrażenie, które pobiera jego adres.

- Funkcja C++ funkcji wbudowanej wypierają wcześniejszą makra typu Function. Zalety korzystania z funkcji wbudowanych przez makra to:

  - Bezpieczeństwo typu. Funkcje wbudowane podlegają takie samomu sprawdzaniu typu jak normalne funkcje. Makra nie są bezpieczne dla typów.

  - Poprawna obsługa argumentów z efektami ubocznymi. Funkcje wbudowane obliczają wyrażenia dostarczone jako argumenty przed wprowadzeniem treści funkcji. W związku z tym nie istnieje prawdopodobieństwo, że wyrażenie z efektami ubocznymi nie będzie bezpieczne.

Aby uzyskać więcej informacji na temat funkcji wbudowanych, zobacz [inline \_, __inline, _forceinline](../cpp/inline-functions-cpp.md).

W celu zapewnienia zgodności z poprzednimi wersjami wszystkie obiekty preprocesora, które istniały w C++ standardzie ANSI C i C++we wcześniejszych specyfikacjach, są zachowywane dla firmy Microsoft.

## <a name="see-also"></a>Zobacz także

[Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)\
[Makra (C/C++)](../preprocessor/macros-c-cpp.md)
