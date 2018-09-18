---
title: Błąd krytyczny C1128 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1128
dev_langs:
- C++
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a0b0c308811b642e0064304cab0688215ac949a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079651"
---
# <a name="fatal-error-c1128"></a>Błąd krytyczny C1128

Liczba sekcji przekroczyła limit formatu pliku obiektowego: skompiluj z parametrem/bigobj

Plik .obj przekracza liczbę sekcji dopuszczalny rozmiar, ograniczenia formatu pliku obiektu COFF.

Osiągnięcie tego ograniczenia sekcji mogą być wynikiem przy użyciu [/Gy](../../build/reference/gy-enable-function-level-linking.md) i kompilacji debugowania; **/Gy** niektóre funkcje przejść do ich własnej sekcji COMDAT. Do kompilacji debugowanej Brak sekcji informacji o debugowaniu dla poszczególnych funkcji COMDAT.

Również może być spowodowany C1128, gdy istnieje zbyt wiele wbudowanych funkcji.

Aby naprawić ten błąd, rozdzielić pliku źródłowego w wielu plikach kodu źródłowego, należy skompilować bez **/Gy**, lub kompilowanie z  [ /bigobj (Zwiększ ilość sekcji w. Plik obj)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  Jeśli użytkownik nie można skompilować przy użyciu **/Gy**, musisz określić optymalizacje pojedynczo, ponieważ **/O2** i **/O1** zarówno implikują **/Gy**.

Jeśli to możliwe należy skompilować bez informacji debugowania.

Może trzeba będzie również mieć określonych wystąpień szablonów w plikach kodu źródłowego w oddzielnych, zamiast konieczności kompilator emisji ich.

Podczas przenoszenia kodu, C1128 prawdopodobnie pojawi się pierwszy podczas korzystania z x64 kompilatora i znacznie później za pomocą x86 kompilatora. x64 będzie miał co najmniej 4 sekcje skojarzone z każdą funkcję skompilowany **/Gy** lub śródwierszowa z szablonów lub wbudowane klasy: kodu, pdata oraz debugowanie informacji i prawdopodobnie xdata.  X86 nie będzie miał pdata.