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
ms.openlocfilehash: 47d56641209ea1fe192bf0c32ace7701a1e579dc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054535"
---
# <a name="fatal-error-c1084"></a>Błąd krytyczny C1084

Nie można odczytać pliku typu: 'Plik': komunikat

Ten błąd jest zazwyczaj wynikiem wywołania interfejsu API systemu wewnętrznego nie powiodło się, wprowadzone przez kompilator. Komunikat wyświetlany, kiedy występuje ten błąd często jest generowany przez [_wcserror_s —](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) lub [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage).

Wykonanie poniższych czynności może pomóc w rozwiązaniu C1084:

- Upewnij się, że podany plik istnieje.

- Upewnij się, że odpowiednie uprawnienia zostały ustawione w celu uzyskania dostępu do określonego pliku.

- Upewnij się, składnia wiersza polecenia stosuje reguły, zgodnie z [składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md).

- Upewnij się, że zmienne środowiskowe **TMP** i **TEMP** są poprawnie zestawu, odpowiednie uprawnienia w celu uzyskania dostępu do katalogów tych zmiennych środowiskowych odnoszą się do. Ponadto upewnij się, że dyski odwołuje się **TMP** i **TEMP** zmienne środowiskowe zawierają odpowiednią ilość wolnego miejsca na dysku.

- Jeśli komunikat jest wyświetlany komunikat "zły numer pliku", określony plik może mieć zostały zamknięcia na pierwszym planie podczas kompilowania w tle.

Po wykonaniu powyższych diagnostyki, należy wykonać czystą kompilację.