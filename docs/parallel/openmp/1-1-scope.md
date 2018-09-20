---
title: 1.1 zakres | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81babf799860030f6d398f64b55ed65039de8649
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393535"
---
# <a name="11-scope"></a>1.1 Zakres

Ta specyfikacja obejmuje równoległe skierowana tylko do użytkowników, którym użytkownik jawnie określa akcje, które mają zostać podjęte przez kompilatora i środowiska wykonawczego systemu w celu wykonania programu, w sposób równoległy. Implementacje OpenMP C i C++ nie są wymagane do sprawdzenia zależności, konfliktów, zakleszczenia, wyścigu lub innych problemów, które powoduje wykonanie programu niepoprawne. Użytkownik jest odpowiedzialny za zapewnienie poprawnie wykonuje aplikacji przy użyciu konstrukcje OpenMP C i C++ interfejsu API. W tym dokumencie nie są objęte generowanych przez kompilator automatyczne przetwarzanie równoległe i dyrektywy kompilatora ułatwiają takie przetwarzania równoległego.