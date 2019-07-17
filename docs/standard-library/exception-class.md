---
title: Klasa exception
ms.date: 11/04/2016
f1_keywords:
- exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: 90906469e923d29dd886930bd36944e4292bd9cd
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246068"
---
# <a name="exception-class"></a>Klasa exception

Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych przez niektóre wyrażenia i standardowej biblioteki języka C++.

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

W szczególności, ta klasa bazowa jest katalogiem głównym klas standardowych wyjątków zdefiniowanych w [ \<stdexcept >](../standard-library/stdexcept.md). Wartość zwrócona przez obiekt string, C `what` jest określony przez konstruktora domyślnego, ale mogą być określone przez konstruktory dla niektórych klas pochodnych w postaci ciągu zdefiniowane w implementacji C. Żadna z funkcji elementu członkowskiego generuje żadnych wyjątków.

**Int** parametr umożliwia określenie, że pamięć nie powinna zostać przydzielona. Wartość **int** jest ignorowana.

> [!NOTE]
> Konstruktory `exception(const char* const &message)` i `exception(const char* const &message, int)` są rozszerzenia Microsoft do standardowej biblioteki języka C++.

## <a name="example"></a>Przykład

Przykłady użycia, które dziedziczą z klasy wyjątku standardowa `exception` , zobacz jedną z klas zdefiniowanych w [ \<stdexcept >](../standard-library/stdexcept.md).
