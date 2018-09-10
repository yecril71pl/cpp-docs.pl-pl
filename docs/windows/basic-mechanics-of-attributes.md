---
title: Podstawowa mechanika atrybutów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], inserting in code
- attributes [C++/CLI], about attributes
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6f6563d61988beb5df91ce0a3ccb871e3a5a9adc
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315954"
---
# <a name="basic-mechanics-of-attributes"></a>Podstawowa mechanika atrybutów

Istnieją trzy sposoby, aby wstawić atrybuty do projektu. Po pierwsze można wstawić je ręcznie w kodzie źródłowym. Po drugie można wstawić je przy użyciu siatki właściwości obiektu w projekcie. Na koniec można wstawić je przy użyciu różnych kreatorów. Aby uzyskać więcej informacji na temat korzystania z **właściwości** okna i różne kreatory, zobacz [tworzenie i zarządzanie projekty języka Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).

Jako wcześniej, gdy projekt jest kompilowany, w którym kompilator analizuje każdego pliku źródłowego języka C++, tworzenie pliku obiektu. Jednak gdy kompilator napotka atrybutu, jest analizowany i składniowo zweryfikowane. Kompilator dynamicznie wywołuje dostawcę atrybutu Wstaw kod lub wprowadzić inne zmiany w czasie kompilacji. Implementacja dostawcy różni się w zależności od typu atrybutu. Na przykład związane z ATL atrybuty są implementowane przez Atlprov.dll.

Na poniższym rysunku pokazano relację między kompilatora i dostawcy atrybutu.

![Atrybut komunikacji](../windows/media/vccompattrcomm.gif "vcCompAttrComm")

> [!NOTE]
> Użycie atrybutu nie zmienia zawartość pliku źródłowego. Jedyną sytuacją, w których atrybut wygenerowanego kodu jest widoczny jest podczas sesji debugowania. Ponadto dla każdego pliku źródłowego w projekcie można wygenerować plik tekstowy, który wyświetla wyniki podstawienia atrybutu. Aby uzyskać więcej informacji na temat tej procedury, zobacz [/Fx (Scal wprowadzony kod)](../build/reference/fx-merge-injected-code.md) i [debugowania kodu wprowadzony](/visualstudio/debugger/how-to-debug-injected-code).

Podobnie jak większość konstrukcji języka C++ atrybuty mają zestaw właściwości, który definiuje ich prawidłowego użycia. To jest określany jako kontekst atrybutu i został rozwiązany w tabeli kontekstu atrybutów dla każdego atrybutu odwołanie do tematu. Na przykład [coclass](../windows/coclass.md) atrybut tylko można stosować do istniejącej klasy lub struktury, w przeciwieństwie do [cpp_quote —](../windows/cpp-quote.md) atrybut, który można wstawić w dowolnym miejscu w obrębie pliku źródłowego języka C++.

## <a name="see-also"></a>Zobacz też

[Pojęcia](../windows/attributed-programming-concepts.md)