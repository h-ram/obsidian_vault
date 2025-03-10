```java
import jade.core.Agent;

public class HelloAgent extends Agent {
    protected void setup() {
        System.out.println("Hello! Agent " + getLocalName() + " is ready.");
    }
}
```

```java
import jade.core.Profile;
import jade.core.ProfileImpl;
import jade.core.Runtime;
import jade.wrapper.AgentContainer;
import jade.wrapper.AgentController;
import jade.wrapper.StaleProxyException;

public class App {
    public static void main(String[] args) {
        // Get the JADE runtime
        Runtime rt = Runtime.instance();
		
        // Create a profile for the main container
        Profile profile = new ProfileImpl();
        profile.setParameter(Profile.GUI, "true"); // Enable JADE GUI
		
        // Create the main container
        AgentContainer mainContainer = rt.createMainContainer(profile);
		
        try {
            // Start an agent inside the main container
            AgentController agent1 = mainContainer.createNewAgent(
                    "Agent 1", // Agent name (AID)
                    "Agent_1", // Class name of the agent
                    new Object[] {} // Arguments (empty in this case)
            );

            agent1.start(); // Start the agent
        } catch (StaleProxyException e) {
            e.printStackTrace();
        }
    }
}
```
# **Agent Communication Language (ACL)**
### **Sender** 
```java
ACLMessage msg = new ACLMessage(ACLMessage.INFORM); // Message type
msg.addReceiver(new AID("ReceiverAgent", AID.ISLOCALNAME)); // Set receiver
msg.setContent("Hello, this is a test message!"); // Set message content
send(msg); // Send message
```
**Example:**
```java
import jade.core.Agent;
import jade.core.AID;
import jade.lang.acl.ACLMessage;

public class SenderAgent extends Agent {
    protected void setup() {
        ACLMessage msg = new ACLMessage(ACLMessage.INFORM);
        msg.addReceiver(new AID("ReceiverAgent", AID.ISLOCALNAME));
        msg.setContent("Hello, this is a test message!");
        send(msg);
    }
}
```
### **Receiver** 
```java
import jade.core.Agent;
import jade.core.AID;
import jade.lang.acl.ACLMessage;

ACLMessage msg = new ACLMessage(ACLMessage.INFORM); // Message type
msg.addReceiver(new AID("Agent 1", AID.ISLOCALNAME)); // Set receiver
msg.setContent("Hello, this is a test message!"); // Set message content
send(msg); // Send message
```
**Example:**
```java
import jade.core.Agent;
import jade.lang.acl.ACLMessage;
import jade.core.AID;

public class SenderAgent extends Agent {
    protected void setup() {
        System.out.println(getLocalName() + " started");

        ACLMessage msg = new ACLMessage(ACLMessage.INFORM);
        msg.addReceiver(new AID("ReceiverAgent", AID.ISLOCALNAME));
        msg.setContent("Hello, this is a test message!");
        send(msg);
    }
}
```
---
# **Behaviours**
In JADE, **behaviors** define what an agent does. There are different types of behaviors depending on execution patterns.
## **How to Set Behaviors**
To **set a behavior**, use:
```java
addBehaviour(new YourBehavior());
```
For example:
```java
addBehaviour(new OneShotBehaviour() { ... });
addBehaviour(new CyclicBehaviour() { ... });
```
You can **combine multiple behaviors** in an agent to create complex logic.
## **1. CyclicBehaviour**
Executes indefinitely, responding to events like incoming messages.
- **Runs continuously** in a loop.
- **Stops only when the agent dies.**
**Example: Listening for Messages**
```java
import jade.core.behaviours.CyclicBehaviour;
import jade.core.Agent;
import jade.lang.acl.ACLMessage;

public class MyAgent extends Agent {
    @Override
    protected void setup() {
        addBehaviour(new CyclicBehaviour(this) {
            public void action() {
                ACLMessage msg = receive();
                if (msg != null) {
                    System.out.println("Received: " + msg.getContent());
                } else {
                    block(); // Pause until a message arrives
                }
            }
        });
    }
}
```
---
## **2. OneShotBehaviour**
Executes a **single task** and then terminates.
- **Used for initialization tasks** like setting up an agent.
**Example: Printing a Message Once**
```java
import jade.core.behaviours.OneShotBehaviour;
import jade.core.Agent;

public class MyAgent extends Agent {
    @Override
    protected void setup() {
        addBehaviour(new OneShotBehaviour() {
            public void action() {
                System.out.println("I run only once!");
            }
        });
    }
}
```
---
## **3. TickerBehaviour**
Executes at **fixed time intervals**.
- **Great for periodic tasks**, like monitoring or updating states.
**Example: Polluting Every 5 Seconds**
```java
import jade.core.behaviours.TickerBehaviour;
import jade.core.Agent;

public class PolluterAgent extends Agent {
    @Override
    protected void setup() {
        addBehaviour(new TickerBehaviour(this, 5000) { // Executes every 5 seconds
            protected void onTick() {
                System.out.println("Polluting a random cell...");
            }
        });
    }
}
```
---
## **4. WakerBehaviour**
Executes **once after a specific delay**.
- **Used for delayed actions**, like scheduling future tasks.
**Example: Start Cleaning After 10 Seconds**
```java
import jade.core.behaviours.WakerBehaviour;
import jade.core.Agent;

public class CleanerAgent extends Agent {
    @Override
    protected void setup() {
        addBehaviour(new WakerBehaviour(this, 10000) { // Waits 10 sec
            protected void onWake() {
                System.out.println("Starting to clean...");
            }
        });
    }
}
```
---
## **5. FSMBehaviour**
Manages **complex workflows** by transitioning between states.  
Useful when an agent has different **phases** of execution.
- **Useful for complex agents** with multiple execution phases.
**Example: State-Based Execution**
```java
import jade.core.behaviours.FSMBehaviour;
import jade.core.behaviours.OneShotBehaviour;
import jade.core.Agent;

public class MyAgent extends Agent {
    @Override
    protected void setup() {
        FSMBehaviour fsm = new FSMBehaviour(this);

        // Define states
        fsm.registerFirstState(new OneShotBehaviour() {
            public void action() { System.out.println("State 1: Start"); }
        }, "STATE1");

        fsm.registerState(new OneShotBehaviour() {
            public void action() { System.out.println("State 2: Processing"); }
        }, "STATE2");

        fsm.registerLastState(new OneShotBehaviour() {
            public void action() { System.out.println("State 3: End"); }
        }, "STATE3");

        // Define transitions
        fsm.registerDefaultTransition("STATE1", "STATE2");
        fsm.registerDefaultTransition("STATE2", "STATE3");

        addBehaviour(fsm);
    }
}
```
---
## **6. ParallelBehaviour**
Allows multiple behaviors to run **simultaneously**.
**Example: Polluting and Listening for Messages**
```java
import jade.core.behaviours.ParallelBehaviour;
import jade.core.behaviours.TickerBehaviour;
import jade.core.behaviours.CyclicBehaviour;
import jade.core.Agent;
import jade.lang.acl.ACLMessage;

public class MyAgent extends Agent {
    @Override
    protected void setup() {
        ParallelBehaviour parallel = new ParallelBehaviour();

        // Add a periodic task (polluting every 3 seconds)
        parallel.addSubBehaviour(new TickerBehaviour(this, 3000) {
            protected void onTick() {
                System.out.println("Polluting a new area...");
            }
        });

        // Add a listener for messages
        parallel.addSubBehaviour(new CyclicBehaviour(this) {
            public void action() {
                ACLMessage msg = receive();
                if (msg != null) {
                    System.out.println("Received: " + msg.getContent());
                } else {
                    block();
                }
            }
        });

        addBehaviour(parallel);
    }
}
```
---
## **Which One to Use?**
- **Listening for messages?** → `CyclicBehaviour`
- **One-time setup?** → `OneShotBehaviour`
- **Periodic tasks?** → `TickerBehaviour`
- **Delayed execution?** → `WakerBehaviour`
- **Multiple tasks at once?** → `ParallelBehaviour`
- **State transitions?** → `FSMBehaviour`
