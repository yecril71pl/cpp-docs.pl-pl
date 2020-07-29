---
title: Klasa exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: fd3fb3c48e9501b7aaf90bca14ea98530b245ec0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228274"
---
# <a name="exception-class"></a>Klasa exception

Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych przez niektóre wyrażenia i przez standardową bibliotekę języka C++.

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

W przypadku tej klasy podstawowej jest to katalog główny klas wyjątków standardowych zdefiniowanych w [\<stdexcept>](../standard-library/stdexcept.md) . Wartość ciągu języka C zwrócona przez `what` jest pozostawiana nieokreślona przez Konstruktor domyślny, ale może być zdefiniowana przez konstruktory dla niektórych klas pochodnych jako ciąg języka C zdefiniowany przez implementację. Żadna z funkcji Członkowskich nie zgłasza żadnych wyjątków.

**`int`** Parametr pozwala określić, że żadna pamięć nie powinna być przypisana. Wartość elementu **`int`** jest ignorowana.

> [!NOTE]
> Konstruktory `exception(const char* const &message)` i `exception(const char* const &message, int)` są rozszerzeniami firmy Microsoft do standardowej biblioteki języka C++.

## <a name="example"></a>Przykład

Aby zapoznać się z przykładami użycia klas wyjątków standardowych, które dziedziczą z `exception` klasy, zobacz dowolną z klas zdefiniowanych w [\<stdexcept>](../standard-library/stdexcept.md) .
