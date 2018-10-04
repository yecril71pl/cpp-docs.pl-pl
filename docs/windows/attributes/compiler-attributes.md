---
title: Atrybuty kompilatora (C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9f0483676fd0dd60d893f8931511083d369539dd
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789598"
---
# <a name="compiler-attributes"></a>Atrybuty kompilatora

Atrybuty kompilatora oferują różne funkcje.

|Atrybut|Opis|
|---------------|-----------------|
|[emitidl](emitidl.md)|Określa, czy wszystkie kolejne atrybuty IDL zostanie przetworzone i umieszczony w pliku .idl wygenerowany.|
|[event_receiver](event-receiver.md)|Tworzy odbiorca zdarzenia.|
|[event_source](event-source.md)|Tworzy źródła zdarzenia.|
|[export](export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|
|[Implementuje](implements-cpp.md)|Określa interfejsach wysyłki, które muszą być składowymi typu klasy coclass IDL.|
|[importidl](importidl.md)|Wstawia pliku .idl określony w pliku .idl wygenerowany.|
|[importlib](importlib.md)|Sprawia, że typy, które już zostały skompilowane do do biblioteki typów, trwa tworzenie innej biblioteki typów.|
|[includelib —](includelib-cpp.md)|Powoduje, że pliku .idl lub .h, mają zostać uwzględnione w pliku .idl wygenerowany.|
|[library_block](library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|
|[no_injected_text](no-injected-text.md)|Zabezpiecza kompilator przed wprowadzanie kodu w wyniku użycia atrybutu.|
|[satype](satype.md)|Określa typ danych `SAFEARRAY`.|
|[Wersja](version-cpp.md)|Identyfikuje określoną wersję spośród wielu wersji interfejsu lub klasy.|

## <a name="see-also"></a>Zobacz też

[Atrybuty według grup](attributes-by-group.md)