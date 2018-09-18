---
title: Obsługa wolnych wątków w dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bf12ffedca5140193564dc6a9a49203ced6d870a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087997"
---
# <a name="supporting-free-threading-in-your-provider"></a>Obsługa wolnych wątków w dostawcy

Wszystkie klasy dostawcy OLE DB są odporne na wątki i wpisy rejestru są odpowiednio ustawiane. To dobry pomysł, aby obsługa wolnych wątków w celu zapewnienia wysokiego poziomu wydajności w sytuacjach, w wielu użytkowników. Aby zapewnić dostawcą metodą o bezpiecznych wątkach, należy sprawdzić, czy kod jest zablokowany prawidłowo. Zawsze, gdy zapisu lub przechowywania danych, należy zablokować dostęp za pomocą sekcji krytycznych.  
  
Każdy obiekt szablonu dostawcy OLE DB ma swój własny sekcję krytyczną. Aby łatwiej blokowania, każda nowa klasa tworzenia powinna być klasą szablonu, biorąc klasy nadrzędnej nazwę jako argument.  
  
Poniższy przykład pokazuje, jak zablokować kodu:  
  
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
  
Aby uzyskać więcej informacji o tym, jak chronić krytyczne sekcje z `Lock` i `Unlock`, zobacz [wielowątkowość: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
Należy również sprawdzić, czy jakiekolwiek metody zastąpisz (takie jak `Execute`) jest metodą o bezpiecznych wątkach.  
  
## <a name="see-also"></a>Zobacz też  

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)