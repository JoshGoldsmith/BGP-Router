# BGP-Router
BGP Router for CS3700


We used the Python skeleton provided as starter code.
We began with implementing the handle_packet function which dispatches packets to the proper functions based on their type.
We then implemented the three methods, update, forward, and dump.
We chose to represent our routing table as a dictionary with the network as the key
We stored our updates in an array of dictionaries
We didn't realize we had to add the ASN in the milestone and initially had lots of trouble diagnosing our errors.
We also made a mistake in our helper function that we used for forward to select a route from our forwarding table. The mistake caused our function to consistently return the incorrect route. We found our issue using the simulator output to see that we were sending data packets back to the neighbor that forwarded them to us as opposed to the neighbor that held the destination.
