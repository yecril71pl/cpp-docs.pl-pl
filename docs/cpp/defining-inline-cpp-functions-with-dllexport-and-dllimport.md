---
title: Definiowanie funkcji śródwierszowych języka C++ z dllexport i dllimport | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- inline functions [C++], defining
- functions [C++], defining inline
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5299018f8c8e92cd4bfe45889f379c88064007e1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037089"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definiowanie funkcji śródwierszowych języka C++ z dllexport i dllimport

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Można zdefiniować jako wbudowaną funkcję z **dllexport** atrybutu. W takim przypadku funkcja zawsze jest tworzone i wyeksportowane, czy każdy moduł w programie odwołuje się do funkcji. Funkcja zakłada się, że można zaimportować przez inny program.

Można również zdefiniować jako wbudowaną, funkcja zadeklarowana za pomocą **dllimport** atrybutu. W tym przypadku funkcji może być rozwinięte (zależnie od specyfikacji /Ob), ale nigdy nie miała wystąpień. W szczególności podjęcia adresu funkcji wbudowanych zaimportowane adresu funkcji znajdujących się w bibliotece DLL jest zwracana. To zachowanie jest taki sam, jak pobieranie adresu innego niż inline zaimportowane funkcji.

Te reguły dotyczą wbudowane funkcje, których definicje są wyświetlane w ramach definicji klasy. Ponadto statyczne dane lokalne i parametry w funkcji śródwierszowych Obsługa tej samej tożsamości między klientem biblioteki DLL, tak samo jak w jednym programie (czyli plik wykonywalny bez interfejsu biblioteki DLL).

Wykonuje opieki podczas dostarczania funkcji śródwierszowych zaimportowane. Załóżmy na przykład, jeśli zaktualizujesz biblioteki DLL, nie będzie używany przez klienta zmiany wersję biblioteki DLL. Aby upewnić się, że są ładowane właściwe wersję biblioteki DLL, należy odbudować także klienta biblioteki DLL.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[dllexport, dllimport](../cpp/dllexport-dllimport.md)