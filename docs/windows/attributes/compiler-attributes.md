---
title: Atrybuty kompilatora (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
ms.openlocfilehash: ea4d3119a640c0642664210384c297e011104411
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030822"
---
# <a name="compiler-attributes"></a>Atrybuty kompilatora

Atrybuty kompilatora oferują różne funkcje.

|Atrybut|Opis|
|---------------|-----------------|
|[emitidl](emitidl.md)|Określa, czy wszystkie kolejne atrybuty IDL zostanie przetworzone i umieszczony w pliku .idl wygenerowany.|
|[event_receiver](event-receiver.md)|Tworzy odbiorca zdarzenia.|
|[event_source](event-source.md)|Tworzy źródła zdarzenia.|
|[export](export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|
|[implements](implements-cpp.md)|Określa interfejsach wysyłki, które muszą być składowymi typu klasy coclass IDL.|
|[importidl](importidl.md)|Wstawia pliku .idl określony w pliku .idl wygenerowany.|
|[importlib](importlib.md)|Sprawia, że typy, które już zostały skompilowane do do biblioteki typów, trwa tworzenie innej biblioteki typów.|
|[includelib](includelib-cpp.md)|Powoduje, że pliku .idl lub .h, mają zostać uwzględnione w pliku .idl wygenerowany.|
|[library_block](library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|
|[no_injected_text](no-injected-text.md)|Zabezpiecza kompilator przed wprowadzanie kodu w wyniku użycia atrybutu.|
|[satype](satype.md)|Określa typ danych `SAFEARRAY`.|
|[version](version-cpp.md)|Identyfikuje określoną wersję spośród wielu wersji interfejsu lub klasy.|

## <a name="see-also"></a>Zobacz także

[Atrybuty według grup](attributes-by-group.md)