# ai-dlc

The AI-Driven Development Life Cycle: Ideation, Inception, Construction, Operation, with a small mob of broad agents and a person validating at every gate.

**Source.** The method and the agents' responsibilities are taken from [awslabs/aidlc-workflows](https://github.com/awslabs/aidlc-workflows) (MIT-0, v2.11 at the time of writing): the lifecycle, the 11 domain agents, the 2 reviewer agents, and which agent leads or supports each stage. The agents' own text (responsibilities, principles, review questions) is theirs, with the parts about their runtime (state files, audit events, memory paths) removed.

**Team.** `lead` (orchestrator, Claude) conducts the lifecycle and calls `product`, `design`, `delivery`, `architect`, `aws-platform`, `compliance`, `devsecops`, `developer`, `quality`, `pipeline-deploy`, `operations`, and the two reviewers `product-lead` and `architecture-reviewer`. `compliance` and `devsecops` advise and never lead a stage; the reviewers do not change what they review.

**How a run goes.** The lead proposes the plan from the request (the composer's job upstream) and may leave stages out, saying why. People validate at: the end of Ideation; the mob-elaboration points in Inception (requirements and stories, then design and units, then the delivery plan, each after the matching reviewer says READY); each Unit in Construction; and before deployment. At each phase boundary the lead checks traceability and puts what is missing in the gate decision.

**Where it differs from upstream, and why.** Upstream asks for an approval after every stage (33 stages). Krama asks at the points above, because each approval is a decision a person has to make in a UI rather than a prompt in a terminal. The deterministic engine upstream (state file, audit shards, scopes, workflow profiles) is replaced by Krama's run state, audit and the lead's plan; there are no separate workflow profiles, the lead picks the depth from the request. The knowledge and learned-rules features are not included.

**Needs.** The `a2a-claude` backend. No MCP servers.

**Inputs.** The request text: the intent.
