---
title: Błąd krytyczny C1010
ms.date: 08/19/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 35b0f60f7eb3be887598e7ffaf3e3eae74aefcff
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630789"
---
# <a name="fatal-error-c1010"></a>Błąd krytyczny C1010

nieoczekiwany koniec pliku podczas wyszukiwania prekompilowanego nagłówka. Czy zapomnisz dodać "#include Name" do źródła?

Plik dołączany określony za pomocą [/Yu](../../build/reference/yu-use-precompiled-header-file.md) nie znajduje się na liście w pliku źródłowym.  Ta opcja jest domyślnie włączona w większości typów projektów programu C++ Visual Studio i *PCH. h* (*stdafx. h* w Visual Studio 2017 i starszych) to domyślny plik dołączania określony przez tę opcję.

W środowisku programu Visual Studio Użyj jednej z następujących metod, aby rozwiązać ten problem:

- Jeśli nie używasz prekompilowanych nagłówków w projekcie, ustaw właściwość **Utwórz/Użyj prekompilowanego nagłówka** plików źródłowych, aby nie używał **prekompilowanych nagłówków**. Aby ustawić tę opcję kompilatora, wykonaj następujące kroki:

   1. W okienku Eksplorator rozwiązań projektu kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie **Właściwości**.

   1. W lewym okienku kliknij folder **C/C++**  .

   1. Kliknij węzeł **prekompilowane nagłówki** .

   1. W okienku po prawej stronie kliknij pozycję **Utwórz/Użyj prekompilowanego nagłówka**, a następnie kliknij przycisk **nie używa prekompilowanych nagłówków**.

- Upewnij się, że nie usunięto przypadkowo pliku nagłówkowego, zmieniono jego nazwę (domyślnie stdafx. h) z bieżącego projektu. Ten plik należy również uwzględnić przed jakimkolwiek innym kodem w plikach źródłowych przy użyciu **#include "stdafx. h"** . (Ten plik nagłówka jest określany jako **Tworzenie/używanie PCH przez** właściwość projektu pliku)