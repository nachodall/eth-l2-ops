# Ethrex L2 Bridge Demonstration

Proof of execution for deploying and interacting with an Ethrex L2 vanilla rollup on the Hoodi testnet.

## Video Demonstration
[Link to YouTube Video](https://youtu.be/BP2PALxuTDA)

Demonstrated workflow:
1. Ethrex execution client running as an L2 rollup.
2. Prover client running in `exec` mode.
3. L1 to L2 token deposit.
4. L2 to L2 internal transfer.
5. L2 to L1 token withdrawal.

## Technical Setup

### Proxy Implementation

To ensure stable communication between the Ethrex L2 node and the Hoodi L1 network, we use a RPC proxy. The external L1 RPC endpoint occasionally rejects direct requests from the Rust client or drops connections unexpectedly. This custom middleware solves this by intercepting the JSON-RPC traffic, injecting mandatory HTTP headers (such as Content-Type and User-Agent), and silently handling connection errors. This prevents the L2 sequencer from crashing and guarantees a seamless integration during the bridge lifecycle.
