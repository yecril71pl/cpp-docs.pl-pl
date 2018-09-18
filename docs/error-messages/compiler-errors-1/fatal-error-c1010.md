---
title: Błąd krytyczny C1010 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1010
dev_langs:
- C++
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae762c15c96ed7c12a20d2070d22cdc556667ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064090"
---
# <a name="fatal-error-c1010"></a>Błąd krytyczny C1010

Nieoczekiwany koniec pliku podczas wyszukiwania prekompilowanego pliku nagłówkowego. Czy zapomniano dodać "#include nazwę" do źródła?

Określony za pomocą pliku dołączanego [/Yu](../../build/reference/yu-use-precompiled-header-file.md) nie znajduje się w pliku źródłowym.  Ta opcja jest włączona domyślnie w większości typów projektów Visual C++, a "w pliku stdafx.h" jest domyślnie zawierają plik określony przez tę opcję.

W środowisku Visual Studio użyj jednej z następujących metod Aby rozwiązać ten problem:

- Jeśli nie używasz wstępnie skompilowanych nagłówków w projekcie, ustaw **Utwórz/użycie prekompilowanego pliku nagłówkowego** własności plików źródłowych **nie za pomocą wstępnie skompilowanych nagłówków**. Aby ustawić tę opcję kompilatora, wykonaj następujące kroki:

   1. W okienku projekt w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**.

   1. W okienku po lewej stronie kliknij **C/C++** folderu.

   1. Kliknij przycisk **prekompilowanych nagłówków** węzła.

   1. W okienku po prawej stronie kliknij **Utwórz/użycie Prekompilowanego nagłówka**, a następnie kliknij przycisk **nie przy użyciu prekompilowanych nagłówków**.

- Upewnij się, że możesz nie przypadkowo usunięte, zmieniono nazwę lub usunięty plik nagłówkowy (domyślnie stdafx.h) z bieżącego projektu. Ten plik również musi być umieszczony przed innymi kodami w plikach źródłowych przy użyciu **#include "stdafx.h"**. (Ten plik nagłówkowy jest określony jako **Utwórz/Użyj PCH za pośrednictwem pliku** właściwość projektu)