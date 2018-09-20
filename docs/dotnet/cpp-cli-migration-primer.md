---
title: C + +/ CLI Podręcznik migracji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++/CLI Version 2
- upgrading Visual C++ applications, Managed Extensions for C++ to Visual C++ 2005 syntax
- migration [C++], C++/CLI Version 2
- Managed Extensions for C++, upgrading syntax
- C++/CLI Version 2, managed extensions
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 88b32ea226971c0fa5b6d269a8992629c3c4de77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385434"
---
# <a name="ccli-migration-primer"></a>Podręcznik migracji C++/CLI

Jest to przewodnik do przenoszenia programów Visual C++ z zarządzanych rozszerzeń dla C++ do Visual C++.

C + +/ CLI rozszerza paradygmat programowania dynamicznego składnika języka standard ISO C++. Nowy język oferuje szereg znaczne ulepszenia w stosunku do rozszerzeń zarządzanych. Ta sekcja zawiera listę zarządzanych rozszerzeń dla funkcji języka C++ i ich mapowanie do programu Visual C++, gdzie takie mapowanie istnieje i wykazuje te konstrukcje, dla których nie istnieje żadne mapowanie.

## <a name="in-this-section"></a>W tej sekcji

[Zarys zmian (C++/CLI)](../dotnet/outline-of-changes-cpp-cli.md)<br/>
Zaawansowany konspekt dla szybkiego odwołania, zapewniający listę zmian w pięciu kategoriach ogólnych.

[Słowa kluczowe języka (C++/CLI)](../dotnet/language-keywords-cpp-cli.md)<br/>
W tym artykule omówiono zmiany słów kluczowych języka, w tym zniesienie podwójnego podkreślenia i wprowadzenie zarówno kontekstowych, jak i odstępów między słowami kluczowymi.

[Typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)<br/>
Zmiany syntaktyczne w deklaracji wspólnego systemu typu (CTS) — obejmuje to zmiany w deklaracji klas, tablic (w tym tablicy parametru), typów wyliczeniowych i tak dalej.

[Deklaracje składowych w obrębie klasy lub interfejsu (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
Przedstawia zmiany dotyczące elementów członkowskich klasy takich jak właściwości skalarne, właściwości indeksu, operatory, delegaty i zdarzenia.

[Typy wartości i ich zachowania (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
Koncentruje się na typach wartości i nowej rodzinie wskaźników wnętrza i przypinania. Omawia także szereg istotnych zmian semantycznych takich jak wprowadzenie niejawnego opakowania, niezmienność opakowanych typów wartości i usunięcie obsługi konstruktorów domyślnych w obrębie klas wartości.

[Ogólne zmiany w języku (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
Szczegóły semantyczne zmian takich jak obsługa notacji oddanych ciągu literału zachowanie i zmiany w semantyce między ISO C++ i C + +/ interfejsu wiersza polecenia.

## <a name="see-also"></a>Zobacz też

[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)