---
title: Błąd krytyczny C1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: e57e4e0899a5f9d81e87a203b1b699cef0884f0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203271"
---
# <a name="fatal-error-c1311"></a>Błąd krytyczny C1311

Format COFF statycznie nie może zainicjować "var" z liczbą bajtów adresu

Adres, którego wartość nie jest znana w czasie kompilacji, nie może być statycznie przypisany do zmiennej, której typ ma magazyn mniejszy niż 4 bajty.

Ten błąd może wystąpić w kodzie, który jest nieprawidłowy C++.

Poniższy przykład pokazuje jeden warunek, który może powodować C1311.

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```
