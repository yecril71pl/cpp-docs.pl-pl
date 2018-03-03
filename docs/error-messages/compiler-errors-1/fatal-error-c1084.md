---
title: "Błąd krytyczny C1084 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1084
dev_langs:
- C++
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 828486ee2d3057c4d9c658defc1477de49b6cd0e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1084"></a>Błąd krytyczny C1084
Nie można odczytać pliku filetype: 'Plik': wiadomości  
  
 Ten błąd jest zazwyczaj wynikiem wywołania interfejsu API systemu wewnętrznego nie powiodło się, przez kompilator. Komunikat wyświetlany po wystąpieniu tego błędu jest często generowane przez [_wcserror_s —](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) lub [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351.aspx).  
  
 Wykonaj następujące czynności mogą pomóc w rozwiązaniu C1084:  
  
-   Upewnij się, że podany plik istnieje.  
  
-   Upewnij się, że są ustawione odpowiednie uprawnienia, aby uzyskać dostęp do określonego pliku.  
  
-   Upewnij się, składni wiersza polecenia jest zgodna z regułami zgodnie z [składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md).  
  
-   Upewnij się, że zmienne środowiskowe **TMP** i **TEMP** są poprawnie zestawu, a także odpowiednie uprawnienia w celu uzyskania dostępu do katalogów dotyczą te zmienne środowiskowe. Ponadto upewnij się, że dyski odwołuje się **TMP** i **TEMP** zmiennych środowiskowych zawiera odpowiednią ilość wolnego miejsca.  
  
-   Jeśli komunikat jest wyświetlany komunikat "zły numer pliku" określony plik może mieć zostały zamykania na pierwszym planie podczas kompilowania w tle.  
  
 Po wykonaniu powyższych diagnostyki, wykonać czystą kompilację.