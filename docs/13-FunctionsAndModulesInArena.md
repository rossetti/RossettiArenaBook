\cleardoublepage 

# Arena Operators, Functions, Distributions, and Modules {#app:ArenaOFD}

## Arena Mathematical and Logical Operators

::: {#tab:MathLogicOperators}
  **Operator**            **Operation**                          **Priority**
  ----------------------- ------------------------------------- --------------
  **Math Operators**                                            
  $\ast\ast$              Exponentiation                          1(highest)
  $/$                     Division                                    2
  $\ast$                  Multiplication                              2
  \-                      Subtraction                                 3
  \+                      Addition                                    3
  **Logical Operators**                                         
  .EQ., ==                Equality comparison                         4
  .NE.,$<>$               Non-equality comparison                     4
  .LT.,$<$                Less than comparison                        4
  .GT.,$>$                Greater than comparison                     4
  .LT.,$<=$               Less than or equal to comparison            4
  .GE.,$>=$               Greater than or equal to comparison         4
  .AND.,&&                Conjunction (and)                           5
  .OR.,$\|$               Inclusive disjunction (or)                  5

  Table: (\#tab:MathLogicOperators) Mathematical and Logical Operators
:::

\newpage

::: {#tab:ArenaMathFunc}
  **Function**                                   **Description**
  ---------------------- ---------------------------------------------------------------
  ABS(a)                                         Absolute value
  ACOS(a)                                          Arc cosine
  AINT(a)                                           Truncate
  AMOD(a1, a2)            Real remainder, returns(a1-(AINT($\frac{a1}{a2}$)$\times$a2))
  ANINT(a)                                  Round to nearest integer
  ASIN(a)                                           Arc sine
  ATAN(a)                                          Arc tangent
  COS(a)                                             Cosine
  EP(a)                                        Exponential($e^a$)
  HCOS(a)                                       Hyperbolic cosine
  HSIN(a)                                        Hyperbolic sine
  HTAN(a)                                      Hyperbolic tangent
  MN(a1, a2, $\ldots$)                            Minimum value
  MOD(a1,a2)                            same as AMOD(AINT(a1), AINT(a2))
  MX(a1, a2, $\ldots$)                            Maximum value
  LN(a)                                         Natural logarithm
  LOG(a)                                        Common logarithm
  SIN(a)                                              Sine
  SQRT(a)                                          Square root
  TAN(a)                                             Tangent

  Table: (\#tab:ArenaMathFunc) Arena's Mathematical Functions
:::

\newpage

## Arena Probability Distributions Functions

::: {#tab:ArenaDistributions}
  ---------------------- -----------------------------------------------------
  Beta                   BETA(Alpha, Alpha2`[,Stream`])
  Normal                 NORM(Mean,SD`[,Stream`])
  Empirical Continuous   CONT(Prob1,Value1,Prob2,Value2,$\ldots$`[,Stream`])
  NSExpo                 Non-homogeneous Poisson process
  Empirical Discrete     DISC(Prob1,Value1,Prob2,Value2,$\ldots$`[,Stream`])
  Poisson                POIS(Mean`[,Stream`])
  K-Erlang               ERLA(Mean,k`[,Stream`])
  Lognormal              LOGN(LogMean,LogStd`[,Stream`])
  Uniform(0,1)           RA
  Exponential            EXPO(Mean`[,Stream`])
  Triangular             TRIA(Min,Mode,Max`[,Stream`])
  Gamma                  GAMM(scale,shape`[,Stream`])
  Uniform                UNIF(Min,Max`[,Stream`])
  Johnson                JOHN(shape1,shape2,scale,location`[,Stream`])
  Weibull                WEIB(scale,shape`[,Stream`])
  ---------------------- -----------------------------------------------------

  Table: (\#tab:ArenaDistributions) Arena's Distributions
:::

\newpage


## Basic Process Panel Modules

\footnotesize

::: {#tab:ABPPM}
  ---------- -----------------------------------------------------------------------------------------------------------
  CREATE     Used to create and introduce entities into the model according to a pattern.
  DISPOSE    Used to dispose of entities once they have completed their activities within the model.
  PROCESS    Used to allow an entity to experience an activity with the possible use of a resource.
  ASSIGN     Used to make assignments to variables and attributes within the model
  RECORD     Used to capture and tabulate statistics within the model.
  BATCH      Used to combine entities into a permanent or temporary representative entity.
  SEPARATE   Used to create duplicates of an existing entity or to split a batched group of entities.
  DECIDE     Used to provide alternative flow paths for an entity based on probabilistic or condition based branching.
  VARIABLE   Used to define variables for use within the model.
  RESOURCE   Used to define a quantity of units of a resource that can be seized and released by entities.
  QUEUE      Used to define a waiting line for entities whose flow is currently stopped within the model.
  ENTITY     Used to define different entity types for use within the model.
  SET        Used to define a list of elements within Arena that can be indexed by the location in the list.
  SCHEDULE   Used to define a staffing schedule for resources or a time-based arrival pattern.
  ---------- -----------------------------------------------------------------------------------------------------------

  Table: (\#tab:ABPPM) Basic Process Panel Modules
:::
\normalsize

\newpage

## Advanced Process Panel Modules

\footnotesize

::: {#tab:AAPPM}
  ----------------- ---------------------------------------------------------------------------------------------------------------------------
  SEIZE             Allows an entity to request a number of units of a resource. If the units are not available, the entity waits in a queue.
  DELAY             Allows an entity to experience a delay in movement via the scheduling of an event.
  RELEASE           Releases the units of a resource seized by an entity.
  MATCH             Allows entities to wait in queues until a user specified matching criteria occurs.
  HOLD              Holds entities in a queue until a signal is given or until a condition in the model is met.
  SIGNAL            Signals entities in a HOLD queue to proceed.
  PICKUP            Allows an entity to pick up and place other entities into a group associated with the entity.
  DROPOFF           Allows an entity to drop off entities from its entity group.
  SEARCH            Allows an entity to search a queue for entities that match search criteria.
  REMOVE            Allows an entity to remove other entities directly from a queue.
  STORE             Indicates that the entity is in a STORAGE
  UNSTORE           Indicates that the entity is no longer in a STORAGE
  ADJUST VARIABLE   Adjusts a variable to a target value at a specified rate.
  READWRITE         Allows input and output to occur within the model.
  FILE              Defines the characteristics of the operating system file used within a READWRITE module.
  EXPRESSION        Allows the user to define named logical/mathematical expressions that can be used throughout the model.
  STORAGE           Demarks a location/concept that may contain entities.
  ADVANCED SET      Used to define a list of elements within Arena that can be indexed by the location in the list.
  FAILURE           Used to define unscheduled capacity changes for resources according to a time pattern or a usage indicator.
  STATISTIC         Used to define and manage time-based, observation based, and replication statistics.
  ----------------- ---------------------------------------------------------------------------------------------------------------------------

  Table: (\#tab:AAPPM) Advanced Process Panel Modules
:::

\normalsize
\newpage

## Advanced Transfer Panel Modules
\scriptsize
::: {#tab:AATPM}
  --------------- ---------------------------------------------------------------------------------------------------------------------
  STATION         Allows the marking in the model for a location to which entities can be directed for processing.
  ROUTE           Facilitates the movement between stations with a time delay.
  ENTER           Represents STATION, DELAY, and/or EXIT/FREE
  LEAVE           Represents ROUTE or TRANSPORT or CONVEY with DELAY option
  PICKSTATION     Allows entity to decide on its next station based on conditions.
  ACCESS          Requests space on a conveyor. Entity waits if no space is available.
  CONVEY          After obtaining space on a conveyor, causes the entity to be conveyed to its destination station.
  EXIT            Releases space on a conveyor
  START           Causes a stopped conveyor to start transferring entities.
  STOP            Causes a conveyor to stop transferring entities.
  ALLOCATE        Assigns entity a transporter without moving the transporter, entity controls transporter and may wait in queue.
  MOVE            Moves an allocated transporter to a station destination.
  REQUEST         Asks transporter for pick up, entity waits until transporter is allocated, and transporter moves to pick up location.
  TRANSPORT       Same as REQUEST followed by MOVE to the entities desired location.
  FREE            Causes the entity to release an allocated transporter.
  HALT            Changes the state of the transporter to inactive.
  ACTIVATE        Changes the state of the transporter to active.
  SEQUENCE        Allows pre-specified routes of stations to be defined and attributes to be assigned when entities are transferred.
  CONVEYOR        Defines a conveyor as a list of segments and provides the velocity and space characteristics of the conveyor.
  SEGMENT         Defines the distance between two stations as a segment on a conveyor.
  TRANSPORTER     Defines a mobile resource and its characteristics, capable of free path or guided path movement.
  DISTANCE        Defines the from-to distances between stations for free path transporters.
  NETWORK         Defines a set of transporter links between intersections that represents a guided path network for transporters.
  NETWORKLINK     Defines the characteristics of a space constraining path between intersections within guided path networks.
  ACTIVITY AREA   Defines stations that are part of an area for the collection of aggregate statistics on the group of stations.
  --------------- ---------------------------------------------------------------------------------------------------------------------

  Table: (\#tab:AATPM) Advanced Transfer Panel Modules
:::
\normalsize
\newpage

## Important SIMAN Blocks, Elements, and Pre-Defined Attributes and Variables
\footnotesize
::: {#tab:AMUBAV}
  ----------------------- ---------------------------------------------------------------------------------------------------
  IF-ELSEIF-ELSE-ENDIF    (Blocks panel) Allows standard logic based flow of control.
  WHILE-ENDWHILE          (Blocks panel) Allows for iterative looping.
  BRANCH                  (Blocks panel) Allows probabilistic and condition based path determination and cloning of entities.
  TNOW                    The current simulation time.
  NREP                    Current replication number.
  MREP                    Maximum number of replications.
  J                       Index in SEARCH module
  NQ(queue name)          Number of entities in the named queue.
  MR(resource name)       The current capacity of the named resource
  NR(resource name)       The current number of busy units of the named resource
  Entity.SerialNumber     A number assigned to an entity upon creation. Duplicates will have this same number.
  Enity.Jobstep           The entity's current position in its squence.
  Entity.Sequence         The entity's sequence when using a transfer option.
  Entity.Station          The entity's location or destination.
  Entity.CurrentStation   The entity's location.
  Enity.CreateTime        The value of TNOW when the entity was created.
  IDENT                   A unique number assigned to an entity while in the model. No entities have the same IDENT number.
  ----------------------- ---------------------------------------------------------------------------------------------------

  Table: (\#tab:AMUBAV) Miscellaneous Useful Blocks, Attributes, and Variables
:::
\normalsize

