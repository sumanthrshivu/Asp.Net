# StateManagement Options

| Criteria       | ViewState                                                      | SessionState                                                                                 | ApplicationState                             |
|----------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------|----------------------------------------------|
| Storage        | Client-side                                                    | Server-side                                                                                  | Server-side                                  |
| Size           | Minimal-as with the form post this data is sent back and forth | can be any size, but should be minimized since every user has thier own separete session store.                                                                             | can be any size-it will only be stored once. |
| Security       | Not very secure                                                           | secured                                                                                        | secured                                        |
| Accessibility  | Single user                                                       | Single user                                                                                     | All users                                    |
| Timeout Period | Single WebForm                                                    | As long as the user is active and timeout period( typically 20mins )but we can configure it. | Untill the application close.                |
                                             
## Usecase
### ViewState: 
View state should be used when the user needs to store a small amount of data at the client browser with faster retrieval. The developer should not use this technique to retain state with larger data since it will create a performance overhead for the webpage. It should be used for sending data from one page to another. Not very secure to store sensitive information.
 
 ### SessionState
 In Proc mode is best suited for the application that is hosted on a single server and mid size use base or the session variable used is not big, to avoid data loss and scalability issues. When there is a requirement for a web farm  or web garden deployments the “out of process “modes like state server or SQL Server modes are the best option.
 
 ### ApplicationState
 An application variable is used only when the variable needs to have global access and when you need them for the entire time, during the lifetime of an application.
