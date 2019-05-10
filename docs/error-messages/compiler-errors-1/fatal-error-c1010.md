---
title: Błąd krytyczny C1010
ms.date: 11/04/2016
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 204c7ef94d82513338f6635ec9eb22f26fc090a7
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448020"
---
# <a name="fatal-error-c1010"></a>Błąd krytyczny C1010

Nieoczekiwany koniec pliku podczas wyszukiwania prekompilowanego pliku nagłówkowego. Czy zapomniano dodać "#include nazwę" do źródła?

Określony za pomocą pliku dołączanego [/Yu](../../build/reference/yu-use-precompiled-header-file.md) nie znajduje się w pliku źródłowym.  Ta opcja jest włączona domyślnie w programie Visual Studio w większości C++ typów projektów i "w pliku stdafx.h" jest domyślnie zawierają plik określony przez tę opcję.

W środowisku Visual Studio użyj jednej z następujących metod Aby rozwiązać ten problem:

- Jeśli nie używasz wstępnie skompilowanych nagłówków w projekcie, ustaw **Utwórz/użycie prekompilowanego pliku nagłówkowego** własności plików źródłowych **nie za pomocą wstępnie skompilowanych nagłówków**. Aby ustawić tę opcję kompilatora, wykonaj następujące kroki:

   1. W okienku projekt w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**.

   1. W okienku po lewej stronie kliknij **C/C++** folderu.

   1. Kliknij przycisk **prekompilowanych nagłówków** węzła.

   1. W okienku po prawej stronie kliknij **Utwórz/użycie Prekompilowanego nagłówka**, a następnie kliknij przycisk **nie przy użyciu prekompilowanych nagłówków**.

- Upewnij się, że możesz nie przypadkowo usunięte, zmieniono nazwę lub usunięty plik nagłówkowy (domyślnie stdafx.h) z bieżącego projektu. Ten plik również musi być umieszczony przed innymi kodami w plikach źródłowych przy użyciu **#include "stdafx.h"**. (Ten plik nagłówkowy jest określony jako **Utwórz/Użyj PCH za pośrednictwem pliku** właściwość projektu)