---
title: Błąd krytyczny C1211
ms.date: 11/04/2016
f1_keywords:
- C1211
helpviewer_keywords:
- C1211
ms.assetid: df0ca70d-ec6e-4400-926a-b877e2599978
ms.openlocfilehash: 1e01f75877169225d0e6c20b8a36ce55e3c15c4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203375"
---
# <a name="fatal-error-c1211"></a>Błąd krytyczny C1211

Atrybut niestandardowy TypeForwardedTo nie jest obsługiwany przez zainstalowaną wersję środowiska uruchomieniowego w trakcie wykonania

C1211 występuje, gdy masz kompilator dla bieżącej wersji, ale środowisko uruchomieniowe języka wspólnego z poprzedniej wersji.

Niektóre funkcje kompilatora mogą nie działać w poprzedniej wersji czasu wykonywania.

Aby rozwiązać C1211, zainstaluj środowisko uruchomieniowe języka wspólnego, które zostało dostarczone z używanym kompilatorem.

Aby uzyskać więcej informacji, zobacz [przekazywanie typuC++(/CLI)](../../extensions/type-forwarding-cpp-cli.md).
