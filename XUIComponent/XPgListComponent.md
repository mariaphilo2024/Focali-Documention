## XPgListComponent📖

`XPgListComponent` is a dynamic, reusable Angular component designed to render list-based views for entities. It integrates with configuration options like entity name, detail components, and callbacks to customize behavior and layout. Ideal for rapid UI generation, it supports dependency injection for flexible use in various contexts.

### Code Example📝

```
 loadComponent() {
    this.component = XPgListComponent;
    this.injector = Injector.create({
      providers: [
        {
          provide: XPgListParamProvider,
          useValue: new XPgListParam({
            entityName: 'tenantinfo',
            onInit: (list: ListService<PagedRequestDto>, instance: XPgListComponent) => {
              this.list = list;
              instance.onCreate.subscribe(async value => {
                if (value?.pageMode == 'update') {
                  console.log(value);
                  const tenantInfo = value.item as TenantInfoDto;
                  await this.tenantInfoService.createTenantUserProfile(tenantInfo.tenantId).toPromise();
                }
              });
            },
          } as XpgListPageConfig),
        },
      ],
      parent: this.inj,
    });
  }
```

###  Function Purpose
- The `loadComponent` function dynamically loads a component (`XPgListComponent`) and injects the required dependencies using Angular's `Injector`.
  
### Setting the Component
- This assigns the XPgListComponent as the component to be dynamically loaded.
- XPgListComponent is likely a reusable component for displaying a list.

  ### Creating a Custom Injector
- `Injector.create`: This creates a custom injector for dependency injection.
- `providers`: Specifies the dependencies to inject. Here, the `XPgListParamProvider` is provided.
- `useValue`: Passes a new instance of `XPgListParam` to configure the injected dependency.
-  `provide: XPgListParamProvider` The provide key in the injector configuration specifies the dependency token that Angular 
     will use to inject the service or value.

  ### Configuration for the List Component
  - Defines the name of the entity (`tenantinfo`) that the list component (`XPgListComponent`) will manage.
  - This parameter is likely used by `XPgListComponent` to fetch and display the correct data.
 
  ### `onInit` Callback
  - A callback function executed when the list is initialized.
  -  Provides:
         - `list`: Instance of `ListService`, managing the list data.
         - `instance`: Instance of the `XPgListComponent`.
     
  ### Handling the onCreate Event
 - Subscribes to the `onCreate` event of the `XPgListComponent`.
  - **Purpose**: Handles actions like creation or updating within the list.

### Setting the Parent Injector `parent: this.inj,`
- Specifies the parent injector for the custom injector.
- This ensures dependencies already available in the parent injector can still be resolved

  ### XpgListPageConfig Properties🧩

| **Property**         | **Type**                      | **Function**                                                                                     |
|-----------------------|-------------------------------|--------------------------------------------------------------------------------------------------|
| `entityName`          | `string`                     | Name of the entity to be displayed or managed.                                                  |
| `headerRight`         | `TemplateRef<any>`           | A template reference for custom content in the header's right section.                          |
| `actions`             | `TemplateRef<any>[]`         | Array of template references for custom actions in the component.                               |
| `headerTemplate`      | `TemplateRef<any>[]`         | Array of template references for custom header content.                                         |
| `onInit`              | `(list: ListService<PagedRequestDto>, instance?: any) => void` | Callback executed when the component initializes.                                               |
| `columns`             | `Property[]`                | List of column configurations for the displayed data.                                           |
| `pageAction`          | `PageActionDto`              | Configuration for actions performed on the page (e.g., navigation or API calls).                |
| `staticFilter`        | `string`                     | Static filter applied to the data being displayed.                                              |
| `path`                | `string`                     | Path or endpoint for the data source.                                                           |
| `pageParams`          | `PageParams`                 | Parameters passed to the page, such as pagination or filters.                                   |
| `additionalData`      | `string`                     | Additional data or metadata required for the page.                                              |
| `enableCheckBox`      | `boolean`                    | Determines whether checkboxes are enabled for item selection.                                   |
| `onSelect`            | `(selectedItems: ItemEntityDto[]) => void` | Callback executed when items are selected.                                                      |
| `betaList`            | `boolean`                    | Indicates if the list is in beta mode (optional feature).                                        |

