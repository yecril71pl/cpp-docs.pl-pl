---
title: 1.1 Zakres
ms.date: 11/04/2016
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
ms.openlocfilehash: f87f631ae2d36662daa2ece4790170c00c5cbeb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449208"
---
# <a name="11-scope"></a>1.1 Zakres

Ta specyfikacja obejmuje równoległe skierowana tylko do użytkowników, którym użytkownik jawnie określa akcje, które mają zostać podjęte przez kompilatora i środowiska wykonawczego systemu w celu wykonania programu, w sposób równoległy. Implementacje OpenMP C i C++ nie są wymagane do sprawdzenia zależności, konfliktów, zakleszczenia, wyścigu lub innych problemów, które powoduje wykonanie programu niepoprawne. Użytkownik jest odpowiedzialny za zapewnienie poprawnie wykonuje aplikacji przy użyciu konstrukcje OpenMP C i C++ interfejsu API. W tym dokumencie nie są objęte generowanych przez kompilator automatyczne przetwarzanie równoległe i dyrektywy kompilatora ułatwiają takie przetwarzania równoległego.