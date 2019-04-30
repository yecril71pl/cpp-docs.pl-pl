---
title: Compiler Error C3859
ms.date: 03/08/2019
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: 9b20224207ba797c6ee93c06404e4d90c3d02525
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391884"
---
# <a name="compiler-error-c3859"></a>Compiler Error C3859

> zakres pamięci wirtualnej dla PCH przekroczona; należy ponownie skompilować przy użyciu opcji wiersza polecenia "-Zm*wartość*" lub nowszej

Pamięć wirtualna przydzielone z prekompilowanego pliku nagłówkowego jest zbyt małe ilości danych, którą kompilator próbuje umieścić w niej. Począwszy od programu Visual Studio 2015 **/Zm** zalecenie jest istotne tylko w przypadku korzystania `#pragma hdrstop` dyrektywy. W pozostałych przypadkach jest fałszywe błędu, który wskazuje problemów wykorzystanie pamięci wirtualnej Windows.

Jeśli korzysta z prekompilowanego pliku nagłówkowego `#pragma hdrstop` dyrektywy, użyj **/Zm** flagi kompilatora, aby określić większa wartość dla prekompilowanego pliku nagłówkowego. W przeciwnym razie należy wziąć pod uwagę zmniejszenie liczby procesów równoległych kompilacji w kompilacji. Aby uzyskać więcej informacji, zobacz [/Zm (Określ wstępnie skompilowany nagłówek Memory Allocation Limit)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).
