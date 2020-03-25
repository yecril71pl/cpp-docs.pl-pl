---
title: Obsługa wolnych wątków w dostawcy
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
ms.openlocfilehash: 50e05b70a782dd343031443540790697e980c994
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209554"
---
# <a name="supporting-free-threading-in-your-provider"></a>Obsługa wolnych wątków w dostawcy

Wszystkie klasy dostawcy OLE DB są bezpieczne dla wątków, a wpisy rejestru są odpowiednio ustawiane. Dobrym pomysłem jest wsparcie bezpłatnego wątku w celu zapewnienia wysokiego poziomu wydajności w sytuacjach wielodostępnych. Aby zapewnić bezpieczeństwo wątków dostawcy, należy sprawdzić, czy kod jest prawidłowo zablokowany. Za każdym razem, gdy zapisujesz lub zapisujesz dane, musisz zablokować dostęp z sekcji krytycznych.

Każdy obiekt szablonu dostawcy OLE DB ma swoją własną sekcję krytyczną. Aby ułatwić blokowanie, każda utworzona nowa klasa powinna być klasą szablonu przyjmującą nazwę klasy nadrzędnej jako argument.

Poniższy przykład pokazuje, jak zablokować kod:

```cpp
template <class T>
class CMyObject<T> : public...

HRESULT MyObject::MyMethod(void)
{
   T* pT = (T*)this;      // this gets the parent class

// You don't need to do anything if you are only reading information

// If you want to write information, do the following:
   pT->Lock();         // engages critical section in the object
   ...;                // write whatever information you wish
   pT->Unlock();       // disengages the critical section
}
```

Aby uzyskać więcej informacji na temat ochrony sekcji krytycznych przy użyciu `Lock` i `Unlock`, zobacz [wielowątkowość: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

Sprawdź, czy wszystkie metody zastępujące (takie jak `Execute`) są bezpieczne dla wątków.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
