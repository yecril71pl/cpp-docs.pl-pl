---
title: Błąd krytyczny C1084
ms.date: 11/04/2016
f1_keywords:
- C1084
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
ms.openlocfilehash: 8c90616165a7b47d4251ace998fd49c613f244b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208818"
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