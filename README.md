# mods-minecraft
В данном проекте, я вам расскажу следующее - что такое модификации, покажу примеры и расскажу что он из себя представляет!

## Моды Minecraft: Путешествие вглубь Разработки

# Введение
Здесь вы найдете структуру проекта, примеры кода, пояснения и рекомендации по разработке модов.

## Файловая Структура
```c
mod/
├── src/
│  └── main/
│    └── java/
│      └── com/
│        └── example/
│          └── mod/
│            ├── Main.java
│            ├── BlockRainbow.java
│            ├── ItemExample.java
│            └── EntityFlyingPig.java
└── assets/
  └── examplemod/
    ├── models/
    │  ├── block/
    │  │  └── rainbow_block.json
    │  └── item/
    │    └── example_item.json
    └── textures/
      └── blocks/
        └── rainbow_block.png
```
# 1. src/main/java/com/example/mod/Main.java
```java
package com.example.mod;

import net.minecraftforge.fml.common.Mod;
import net.minecraftforge.fml.common.Mod.EventHandler;
import net.minecraftforge.fml.common.event.FMLInitializationEvent;
import net.minecraftforge.fml.common.registry.GameRegistry;

@Mod(modid = "examplemod", name = "Example Mod", version = "1.0")
public class Main {

    @EventHandler
    public void init(FMLInitializationEvent event) {
        // Регистрация блоков, предметов, сущностей, рецептов и т.д.
        GameRegistry.registerBlock(BlockRainbow.class, "rainbowBlock");
        GameRegistry.registerItem(ItemExample.class, "exampleItem");
        GameRegistry.registerEntity(EntityFlyingPig.class, "FlyingPig", 0, this, 80, 3, true);
        //  Добавление рецептов крафта:
        GameRegistry.addRecipe(new ItemStack(ItemExample.class, 1),
                "D D",
                " S ",
                " S ",
                'D', new ItemStack(Items.DIAMOND),
                'S', new ItemStack(Items.STICK));
    }
}
```

# 2. src/main/java/com/example/mod/BlockRainbow.java
```java
package com.example.mod;

import net.minecraft.block.Block;
import net.minecraft.block.material.Material;
import net.minecraft.creativetab.CreativeTabs;

public class BlockRainbow extends Block {

    public BlockRainbow() {
        super(Material.ROCK);
        setCreativeTab(CreativeTabs.BUILDING_BLOCKS);
        setUnlocalizedName("rainbowBlock");
    }
}
```

# 3. src/main/java/com/example/mod/ItemExample.java
```java
package com.example.mod;

import net.minecraft.item.Item;

public class ItemExample extends Item {

    public ItemExample() {
        setUnlocalizedName("exampleItem");
    }
}
```

# 4. src/main/java/com/example/mod/EntityFlyingPig.java
```java
package com.example.mod;

import net.minecraft.entity.EntityLivingBase;
import net.minecraft.entity.passive.EntityPig;
import net.minecraft.world.World;

public class EntityFlyingPig extends EntityPig {
    public EntityFlyingPig(World world) {
        super(world);
    }

    @Override
    public boolean isOnGround() {
        return false;
    }
}
```

#  assets/examplemod/models/block/rainbow_block.json
```json
{
  "parent": "block/cube_all",
  "textures": {
    "all": "examplemod:blocks/rainbow_block"
  }
}
```

6. assets/examplemod/textures/blocks/rainbow_block.png
   
```• Текстура блока "Rainbow Block" в формате PNG.```

# Разработка Модов

• Java: Язык программирования, на котором пишутся моды. Важно знать основы Java и использовать IDE, такие как IntelliJ IDEA или Eclipse.

• Forge: Старейший и самый популярный фреймворк для разработки модов для Minecraft. Он предоставляет широкий набор инструментов и API, но может быть более сложным в изучении.

• Fabric: Более новый фреймворк, который более прост в использовании и имеет более современный API. Он ориентирован на более легкую и быструю разработку модов.

# Дополнительная Информация

• Зависимости: Убедитесь, что в файле build.gradle указаны правильные зависимости для вашего мода.

• Сборка: Используйте gradle build для сборки мода в файл .jar.

• Тестирование: Используйте gradle runClient для запуска Minecraft с вашим модом в режиме отладки.

## Заключение

Этот репозиторий Git предоставляет вам все необходимые инструменты и информацию для начала разработки модов для Minecraft. 
- Экспериментируйте, изучайте Forge API, и создавайте собственные уникальные моды, которые расширят мир Minecraft и сделают игру еще более увлекательной.

### Различия Forge/Fabric

• Forge: Старейший и наиболее популярный фреймворк для модов. Он обеспечивает широкий набор инструментов и API, но может быть сложным в изучении.

• Fabric: Более новый и простой фреймворк с более современным API. Он ориентирован на быструю и удобную разработку.

## Дополнительные Советы

• Изучите документацию Forge, Fabric, Одеяла или Пепера в зависимости от выбранного вами фреймворка.

• Используйте IDE с поддержкой Java и Forge/Fabric, например, IntelliJ IDEA или Eclipse.

• Используйте системы контроля версий (например, Git) для отслеживания изменений в коде и сотрудничества с другими разработчиками.

• Присоединяйтесь к сообществу разработчиков модов на форумах, в Discord и на других платформах для обмена опытом и получения помощи.

• Не бойтесь экспериментировать и пробовать новые идеи. Разработка модов - это творческий процесс, и успех зависит от вашего воображения и стремления создавать.
