---
title: Specyfikatory klasy magazynowania z deklaracjami funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
ms.openlocfilehash: 69d6fa2b17523f2bb4068cd05a11265d91750021
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157886"
---
# <a name="storage-class-specifiers-with-function-declarations"></a>Specyfikatory klasy magazynowania z deklaracjami funkcji

Można użyć specyfikatora klasy **static** lub `extern` Storage w deklaracjach funkcji. Funkcje zawsze mają globalne okresy istnienia.

**Specyficzne dla firmy Microsoft**

Deklaracje funkcji na poziomie wewnętrznym mają takie samo znaczenie jak deklaracje funkcji na poziomie zewnętrznym. Oznacza to, że funkcja jest widoczna z punktu deklaracji w pozostałej części jednostki translacji, nawet jeśli jest zadeklarowana w zakresie lokalnym.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Reguły widoczności dla funkcji różnią się nieco od reguł dla zmiennych w następujący sposób:

- Funkcja zadeklarowana jako **static** jest widoczna tylko w pliku źródłowym, w którym jest zdefiniowana. Funkcje w tym samym pliku źródłowym mogą wywołać funkcję **statyczną** , ale funkcje w innych plikach źródłowych nie mogą uzyskać do nich dostępu bezpośrednio według nazwy. Można zadeklarować inną funkcję **statyczną** o tej samej nazwie w innym pliku źródłowym bez konfliktu.

- Funkcje zadeklarowane `extern` jako są widoczne w całym pliku źródłowym w programie (chyba że później ponownie zadeklarujesz taką funkcję jako **statyczną**). Każda funkcja może wywołać `extern` funkcję.

- Deklaracje funkcji, które pomijają specyfikator klasy magazynowania, `extern` są domyślnie.

**Specyficzne dla firmy Microsoft**

Firma Microsoft umożliwia ponowne definiowanie `extern` identyfikatora jako **static**.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Klasy magazynu w języku C](../c-language/c-storage-classes.md)
