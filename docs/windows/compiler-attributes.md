---
title: Atrybuty kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 1c1ce698992f1f34434a476be83da6f4697f619c
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316539"
---
# <a name="compiler-attributes"></a>Atrybuty kompilatora

Atrybuty kompilatora oferują różne funkcje.

|Atrybut|Opis|
|---------------|-----------------|
|[emitidl](../windows/emitidl.md)|Określa, czy wszystkie kolejne atrybuty IDL zostanie przetworzone i umieszczony w pliku .idl wygenerowany.|
|[event_receiver](../windows/event-receiver.md)|Tworzy odbiorca zdarzenia.|
|[event_source](../windows/event-source.md)|Tworzy źródła zdarzenia.|
|[export](../windows/export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|
|[Implementuje](../windows/implements-cpp.md)|Określa interfejsach wysyłki, które muszą być składowymi typu klasy coclass IDL.|
|[importidl](../windows/importidl.md)|Wstawia pliku .idl określony w pliku .idl wygenerowany.|
|[importlib](../windows/importlib.md)|Sprawia, że typy, które już zostały skompilowane do do biblioteki typów, trwa tworzenie innej biblioteki typów.|
|[includelib —](../windows/includelib-cpp.md)|Powoduje, że pliku .idl lub .h, mają zostać uwzględnione w pliku .idl wygenerowany.|
|[library_block](../windows/library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|
|[no_injected_text](../windows/no-injected-text.md)|Zabezpiecza kompilator przed wprowadzanie kodu w wyniku użycia atrybutu.|
|[satype](../windows/satype.md)|Określa typ danych `SAFEARRAY`.|
|[Wersja](../windows/version-cpp.md)|Identyfikuje określoną wersję spośród wielu wersji interfejsu lub klasy.|

## <a name="see-also"></a>Zobacz też

[Atrybuty według grup](../windows/attributes-by-group.md)