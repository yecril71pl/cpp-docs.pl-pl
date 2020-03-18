---
title: Klasa exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: 5bef8190889ae00298760ea395fb524f557c2be2
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446830"
---
# <a name="exception-class"></a>Klasa exception

Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych przez niektóre wyrażenia i przez bibliotekę C++ standardową.

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

W przypadku tej klasy podstawowej jest to katalog główny klas wyjątków standardowych zdefiniowanych w [\<stdexcept >](../standard-library/stdexcept.md). Wartość ciągu języka C zwracana przez `what` pozostaje nieokreślona przez konstruktora domyślnego, ale może być zdefiniowana przez konstruktory dla niektórych klas pochodnych jako ciąg języka C zdefiniowany przez implementację. Żadna z funkcji Członkowskich nie zgłasza żadnych wyjątków.

Parametr **int** pozwala określić, że żadna pamięć nie powinna być przypisana. Wartość **int** jest ignorowana.

> [!NOTE]
> Konstruktory `exception(const char* const &message)` i `exception(const char* const &message, int)` są rozszerzeniami firmy Microsoft C++ do standardowej biblioteki.

## <a name="example"></a>Przykład

Aby zapoznać się z przykładami użycia klas wyjątków standardowych, które dziedziczą z klasy `exception`, zobacz dowolną z klas zdefiniowanych w [\<stdexcept >](../standard-library/stdexcept.md).
