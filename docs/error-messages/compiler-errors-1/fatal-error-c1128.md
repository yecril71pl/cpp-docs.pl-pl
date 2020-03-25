---
title: Błąd krytyczny C1128
ms.date: 11/04/2016
f1_keywords:
- C1128
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
ms.openlocfilehash: 64671c9abe8ed1375df1e91ca7509e6a597366ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203651"
---
# <a name="fatal-error-c1128"></a>Błąd krytyczny C1128

Liczba sekcji przekroczyła limit formatu pliku obiektu: Kompiluj z/bigobj

Plik. obj przekroczył liczbę dozwolonych sekcji, ograniczenie formatu pliku obiektu COFF.

Osiągnięcie tego ograniczenia sekcji może wynikać z używania [/Gy](../../build/reference/gy-enable-function-level-linking.md) i kompilacji debugowania; **/Gy** powoduje, że funkcje przechodzą do swoich własnych sekcji COMDAT. W kompilacji debugowania istnieje sekcja informacji o debugowaniu dla każdej funkcji COMDAT.

C1128 może być również spowodowany tym, że jest zbyt wiele funkcji wbudowanych.

Aby naprawić ten błąd, Podziel plik źródłowy na wiele plików kodu źródłowego, Kompiluj bez **/Gy**lub Kompiluj z [/bigobj (Zwiększ liczbę sekcji w. Plik obj)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  Jeśli nie kompilujesz z **/Gy**, musisz określić optymalizacje pojedynczo, ponieważ **/O2** i **/O1** obydwie oznaczają **/Gy**.

Jeśli to możliwe, Kompiluj bez debugowania informacji.

Może być również konieczne posiadanie określonych wystąpień szablonów w oddzielnych plikach kodu źródłowego, a nie ich emitowanie przez kompilator.

Podczas przenoszenia kodu, C1128 będzie prawdopodobnie najpierw wyświetlany podczas korzystania z kompilatora x64 i znacznie później z kompilatorem x86. Architektura x64 będzie zawierać co najmniej 4 sekcje skojarzone z każdą funkcją skompilowaną **/Gy** lub wbudowaną na podstawie szablonów lub klas wbudowanych: kod, pData i informacje debugowania, a także XData.  X86 nie będzie mieć pdata.
