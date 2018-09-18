---
title: Funkcje globalne kompilatora COM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb769cf1419f7a0142a5eeae348ca432f78fb92a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034144"
---
# <a name="compiler-com-global-functions"></a>Funkcje globalne kompilatora COM

**Microsoft Specific**

Dostępne są następujące procedury:

|Funkcja|Opis|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|Zgłasza [_com_error](../cpp/com-error-class.md) w odpowiedzi na błąd.|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Zastępuje funkcja domyślnej, która służy do obsługi błędów COM.|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Konwertuje `BSTR` wartość `char *`.|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Konwertuje `char *` wartość `BSTR`.|

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)<br/>
[Obsługa kompilatora COM](../cpp/compiler-com-support.md)