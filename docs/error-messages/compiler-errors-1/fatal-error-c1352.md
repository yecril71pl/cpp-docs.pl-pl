---
title: Błąd krytyczny C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: fbba87cea05d666d6dc3a385ca1fe52e143fdb5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329728"
---
# <a name="fatal-error-c1352"></a>Błąd krytyczny C1352

Nieprawidłowe lub uszkodzone MSIL w funkcji "function" z modułu 'Plik'

.Netmodule został przekazany do kompilatora, ale kompilator wykrył uszkodzenie w pliku.  Poproś osobę, kto produkowane .netmodule do badania.

Kompilator nie sprawdza pliki .netmodule dla wszystkich typów uszkodzenia.  Jednak Sprawdź, czy wszystkie ścieżki kontroli w funkcji zawiera instrukcję return.

Aby uzyskać więcej informacji, zobacz [pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).