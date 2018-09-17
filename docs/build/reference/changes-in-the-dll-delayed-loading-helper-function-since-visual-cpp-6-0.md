---
title: Zmiany w bibliotece DLL funkcjach pomocnika opóźnionego załadunku po Visual C++ 6.0 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0caf74f02b005ef65e8ac30750fdf244ddeeed0d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712273"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Zmiany w funkcjach pomocnika opóźnionego załadunku bibliotek DLL po Visual C++ 6.0

Jeśli masz wiele wersji programu Visual C++ na komputerze lub jeśli zdefiniowane własnej funkcji Pomocnik, użytkownik może mieć wpływ zmian wprowadzonych do biblioteki DLL funkcjach pomocnika opóźnionego załadunku. Na przykład:

- **__delayloadhelper —** jest teraz **__delayloadhelper2 —**

- **__pfnDliNotifyHook** jest teraz **__pfnDliNotifyHook2**

- **__pfnDliFailureHook** jest teraz **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL** jest teraz **__FUnloadDelayLoadedDLL2**

> [!NOTE]
>  Jeśli używasz domyślnej funkcji pomocnika, te zmiany nie wpłynie na Ciebie. Brak zmian dotyczących jak wywołać program łączący.

## <a name="multiple-versions-of-visual-c"></a>Wiele wersji programu Visual C++

Jeśli masz wiele wersji programu Visual C++ na komputerze, upewnij się, że konsolidator odpowiada delayimp.lib. Jeśli występuje niezgodność, zostanie wyświetlony błąd konsolidatora, raportowanie, albo `___delayLoadHelper2@8` lub `___delayLoadHelper@8` jako nierozpoznany symbol zewnętrzny. Pierwsza oznacza nowe konsolidatora przy użyciu starego delayimp.lib, i jego oznacza stare konsolidator przy użyciu nowego delayimp.lib.

Jeśli wystąpi błąd konsolidatora nierozwiązane Uruchom [dumpbin /linkermember](../../build/reference/linkermember.md): 1 na delayimp.lib, który będzie zawierać funkcji pomocnika, aby zobaczyć funkcji pomocnika, która jest zdefiniowana zamiast tego. Funkcja pomocnika może być także definiowane w pliku obiektu; Uruchom [dumpbin /symbols](../../build/reference/symbols.md) i poszukaj `delayLoadHelper(2)`.

Jeśli wiesz, że masz program Visual C++ 6.0 łączący następnie:

- Uruchom dumpbin pomocnika obciążenia opóźnienia plik .lib lub .obj, aby ustalić, czy definiuje **__delayloadhelper2 —**. W przeciwnym razie łącze zakończy się niepowodzeniem.

- Zdefiniuj **__delayloadhelper —** opóźnienie załadować pliku .lib lub .obj wyłącza pomocnika.

## <a name="user-defined-helper-function"></a>Funkcja pomocnika zdefiniowanych przez użytkownika

Jeśli zdefiniowane własnej funkcji Pomocnik i korzystają z bieżącej wersji programu Visual C++, wykonaj następujące czynności:

- Zmiana nazwy funkcji pomocnika **__delayloadhelper2 —**.

- Ponieważ wskaźniki w deskryptorze opóźnienie (ImgDelayDescr w delayimp.h) zostały zmienione z adresów bezwzględnych (kanalików) na względnych adresów (RVA), aby działać w oczekiwany sposób w programach zarówno 32 - i 64-bitowych, musisz przekonwertować te wstecz do wskaźników. Wprowadzono nową funkcję: pfromrva —, znaleziono w delayhlp.cpp. Tej funkcji na każde z pól w deskryptorze umożliwia przekonwertować z powrotem na obu wskaźniki 32 - lub 64-bitowy. Funkcję pomocnika obciążenia opóźnienia domyślne w dalszym ciągu być dobrym szablon do użycia jako przykład.

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Załaduj wszystkie Importy dla bibliotek DLL ładowanych z opóźnieniem

Konsolidator może ładować wszystkie Importy z biblioteki DLL, który określiłeś być ładowane z opóźnieniem. Zobacz [ładowania wszystkie Importy dla bibliotek DLL z Delay-Loaded](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Ogólne informacje funkcji Pomocnik](understanding-the-helper-function.md)