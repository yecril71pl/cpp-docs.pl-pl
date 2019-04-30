---
title: Funkcje globalne kompilatora COM
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
ms.openlocfilehash: ac74270cd020aa66ccc14ff314a00b388a038086
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399190"
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