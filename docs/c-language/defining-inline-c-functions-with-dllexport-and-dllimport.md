---
title: Definiowanie funkcji śródwierszowych języka C z dllexport i dllimport
ms.date: 11/04/2016
helpviewer_keywords:
- inline functions [C++], with dllexport and dllimport
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
- dllexport attribute [C++]
ms.assetid: 41418f7c-1c11-470b-bb2e-1f8269a239f0
ms.openlocfilehash: 2e43f01b495a03e4f50295de42afa9b6c6b38173
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234421"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definiowanie funkcji śródwierszowych języka C z dllexport i dllimport

**Microsoft Specific**

Można zdefiniować jako wbudowaną funkcję z `dllexport` atrybutu. W takim przypadku funkcja zawsze jest tworzone i wyeksportowane, czy każdy moduł w programie odwołuje się do funkcji. Funkcja zakłada się, że można zaimportować przez inny program.

Można również zdefiniować jako wbudowaną, funkcja zadeklarowana za pomocą **dllimport** atrybutu. W takim przypadku funkcja mogą być rozwinięty (zależnie od Specyfikacja opcji kompilatora /Ob (wbudowane)), ale nigdy nie miała wystąpień. W szczególności podjęcia adresu funkcji wbudowanych zaimportowane adresu funkcji znajdujących się w bibliotece DLL jest zwracana. To zachowanie jest taki sam, jak pobieranie adresu innego niż inline zaimportowane funkcji.

Statyczne dane lokalne i parametry w funkcji śródwierszowych Obsługa tej samej tożsamości między klientem biblioteki DLL, tak samo jak w jednym programie (czyli plik wykonywalny bez interfejsu biblioteki DLL).

Wykonuje opieki podczas dostarczania funkcji śródwierszowych zaimportowane. Załóżmy na przykład, jeśli zaktualizujesz biblioteki DLL, nie będzie używany przez klienta zmiany wersję biblioteki DLL. Aby upewnić się, że są ładowane właściwe wersję biblioteki DLL, należy odbudować także klienta biblioteki DLL.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Importowanie bibliotek DLL i eksportowanie funkcji](../c-language/dll-import-and-export-functions.md)
