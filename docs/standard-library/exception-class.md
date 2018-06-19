---
title: wyjątek klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- exception
dev_langs:
- C++
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff6bc46fb8776de5f93b623b98f87513e710c603
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843109"
---
# <a name="exception-class"></a>Klasa exception

Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłoszonych przez niektórych wyrażeń i standardowa biblioteka C++.

## <a name="syntax"></a>Składnia

```cpp
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
   };
```

## <a name="remarks"></a>Uwagi

W szczególności ta klasa podstawowa jest katalogiem głównym standardowe wyjątek klas zdefiniowanych w [ \<stdexcept — >](../standard-library/stdexcept.md). Wartość zwrócona przez ciąg C `what` jest określony przez konstruktora domyślnego, ale może być zdefiniowana przez konstruktorów niektórych klas pochodnych jako ciąg C zdefiniowane w implementacji. Brak funkcji Członkowskich generują żadnych wyjątków.

`int` Parametr umożliwia określenie, czy można przydzielić pamięci. Wartość `int` jest ignorowana.

> [!NOTE]
> Konstruktory `exception(const char* const &message)` i `exception(const char* const &message, int)` są rozszerzenia Microsoft do standardowej biblioteki C++.

## <a name="example"></a>Przykład

Przykłady użycia klasy standardowe wyjątków, które dziedziczą z `exception` , zobacz jedną z klas zdefiniowanych w [ \<stdexcept — >](../standard-library/stdexcept.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyjątku >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
