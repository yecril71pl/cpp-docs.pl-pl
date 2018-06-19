---
title: Błąd krytyczny C1084 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1084
dev_langs:
- C++
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7266a2158c3e6ccd02ea82de22c6f90a8b6363d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229392"
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