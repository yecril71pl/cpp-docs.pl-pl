---
title: Zmiany w funkcjach pomocnika opóźnionego załadunku bibliotek DLL po Visual C++ 6.0
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
ms.openlocfilehash: 536729e27c89d068957ea451355957e4a35348ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320607"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Zmiany w funkcjach pomocnika opóźnionego załadunku bibliotek DLL po Visual C++ 6.0

Jeśli masz wiele wersji programu Visual C++ na komputerze lub jeśli zdefiniowano własną funkcję pomocnika, mogą mieć wpływ zmiany wprowadzone w funkcji pomocnika opóźnionego ładowania biblioteki DLL. Przykład:

- **__delayLoadHelper** jest teraz **__delayLoadHelper2**

- **__pfnDliNotifyHook** jest teraz **__pfnDliNotifyHook2**

- **__pfnDliFailureHook** jest teraz **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL** jest teraz **__FUnloadDelayLoadedDLL2**

> [!NOTE]
> Jeśli używasz domyślnej funkcji pomocnika, te zmiany nie będą miały wpływu na Ciebie. Nie ma żadnych zmian dotyczących sposobu wywoływania konsolidatora.

## <a name="multiple-versions-of-visual-c"></a>Wiele wersji programu Visual C++

Jeśli masz wiele wersji programu Visual C++ na komputerze, upewnij się, że konsolidator pasuje delayimp.lib. Jeśli występuje niezgodność, otrzymasz raportowanie błędów konsolidatora `___delayLoadHelper2@8` albo jako `___delayLoadHelper@8` nierozwiązany symbol zewnętrzny. Pierwszy z nich implikuje nowy linker ze starym delayimp.lib, a drugi oznacza stary linker z nowym delayimp.lib.

Jeśli pojawi się nierozwiązany błąd konsolidatora, uruchom [dumpbin /linkermember](linkermember.md):1 na delayimp.lib, który ma zawierać funkcję pomocnika, aby zobaczyć, która funkcja pomocnika jest zdefiniowana zamiast. Funkcja pomocnika może być również zdefiniowana w pliku obiektu; uruchom [dumpbin /symbols](symbols.md) `delayLoadHelper(2)`i poszukaj .

Jeśli wiesz, że masz visual C++ 6.0 konsolidator, a następnie:

- Uruchom plik .lib lub .obj obciążenia obciążenia opóźnienia, aby ustalić, czy definiuje **__delayLoadHelper2**. Jeśli nie, łącze zakończy się niepowodzeniem.

- Zdefiniuj **__delayLoadHelper** w pliku .lib lub .obj pomocnika ładowania opóźnienia.

## <a name="user-defined-helper-function"></a>Funkcja pomocnika zdefiniowana przez użytkownika

Jeśli zdefiniowano własną funkcję pomocnika i używasz bieżącej wersji programu Visual C++, wykonaj następujące czynności:

- Zmień nazwę funkcji pomocnika na **__delayLoadHelper2**.

- Ponieważ wskaźniki w deskryptorze opóźnienia (ImgDelayDescr in delayimp.h) zostały zmienione z adresów bezwzględnych (VA) na adresy względne (RVA) do pracy zgodnie z oczekiwaniami w programach 32- i 64-bitowych, należy przekonwertować je z powrotem na wskaźniki. Wprowadzono nową funkcję: PFromRva, znaleziono w delayhlp.cpp. Za pomocą tej funkcji można użyć każdego z pól w deskryptorze, aby przekonwertować je z powrotem na wskaźniki 32- lub 64-bitowe. Domyślna funkcja pomocnika ładowania opóźnienia nadal jest dobrym szablonem do użycia jako przykład.

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Załaduj wszystkie importy dla biblioteki DLL z opóźnieniem

Konsolidator można załadować wszystkie importy z biblioteki DLL, które zostały określone jako opóźnienie załadowany. Aby uzyskać więcej informacji, zobacz [Ładowanie wszystkich importów dla biblioteki DLL z opóźnieniem.](loading-all-imports-for-a-delay-loaded-dll.md)

## <a name="see-also"></a>Zobacz też

[Ogólne informacje funkcji Pomocnik](understanding-the-helper-function.md)
