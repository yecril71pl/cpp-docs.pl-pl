---
title: C + +/ CLI migracji Elementarz | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++/CLI Version 2
- upgrading Visual C++ applications, Managed Extensions for C++ to Visual C++ 2005 syntax
- migration [C++], C++/CLI Version 2
- Managed Extensions for C++, upgrading syntax
- C++/CLI Version 2, managed extensions
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5861a4931a1241a213157b94ca189c6b95f0fb6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccli-migration-primer"></a>Podręcznik migracji C++/CLI
Jest to przewodnik przenoszenia programy Visual C++ z rozszerzeń zarządzanych dla języka C++ dla Visual C++. Lista kontrolna podsumowanie zmian składni, zobacz [(NOTINBUILD) zarządzanych rozszerzeń Lista kontrolna uaktualnienia składni języka C++](http://msdn.microsoft.com/en-us/edbded88-7ef3-4757-bd9d-b8f48ac2aada).  
  
 C + +/ CLI rozszerza modelu programowania dynamiczne składnika, do standard języka ISO C++. Nowy język udostępnia szereg lepsza za pośrednictwem rozszerzeń zarządzanych. Ta sekcja zawiera wyliczany Lista rozszerzeń zarządzanych dla funkcji języka C++ i ich mapowania dla Visual C++, gdzie istnieje mapowanie programu i wskazuje tych konstrukcji, dla których nie istnieje żadne mapowanie.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarys zmian (C + +/ CLI)](../dotnet/outline-of-changes-cpp-cli.md)  
 WYSOKOPOZIOMOWY zarys krótki przewodnik udostępnia listę zmian w obszarze pięć kategorii Ogólne.  
  
 [Słowa kluczowe języka (C + +/ CLI)](../dotnet/language-keywords-cpp-cli.md)  
 W tym artykule omówiono zmiany słów kluczowych języka, w tym usuwania podwójnego podkreślenia i wprowadzenie zarówno kontekstowe i odstępach słów kluczowych.  
  
 [Typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)  
 Wygląda na składni zmiany w deklaracji wspólnej System typu (CTS) — w tym zmiany w deklaracji klasy, tablic (w tym tablicy parametrów), wyliczenia i tak dalej.  
  
 [Deklaracje członków w obrębie klasy lub interfejsu (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)  
 Przedstawia informacje dotyczące elementów członkowskich klasy, takie jak właściwości skalarne, właściwości indeksu, operatory, delegaci i zdarzenia zmiany.  
  
 [Typy wartości i ich zachowania (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 Skupiono się na typy wartości i nowej rodziny wskaźników wewnętrznych i przypinania. Zawiera omówienie również liczbę semantyki znaczących zmian, takich jak wprowadzenie niejawnej konwersji boxing, immutability spakowanymi typami wartości i usunięcie obsługi domyślnych konstruktorów w klasach wartość.  
  
 [Ogólne zmiany w języku (C + +/ CLI)](../dotnet/general-language-changes-cpp-cli.md)  
 Szczegóły semantycznego zmiany, takie jak obsługa notacji rzutowania ciągu literału zachowanie i zmiany w semantyce między ISO C++ i C + +/ CLI.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)   
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)