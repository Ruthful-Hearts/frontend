<script lang="ts">
    import * as Card from "$lib/components/ui/card";
    import { Button } from "$lib/components/ui/button";
    import { Input } from "$lib/components/ui/input";
    import { Label } from "$lib/components/ui/label";
    import { goto } from "$app/navigation";
    import * as Form from "$lib/components/ui/form";
    import { Checkbox } from "$lib/components/ui/checkbox";

    let email = "";
    let password = "";
    let confirmPassword = "";
    let fullName = "";
    let acceptTerms = false;

    async function handleSubmit() {
        // TODO: Implement registration logic
        console.log("Registration attempt:", { email, password, fullName });
    }
</script>

<div class="min-h-screen flex items-center justify-center bg-pink-50">
    <Card.Root class="w-[400px]">
        <Card.Header>
            <Card.Title class="text-2xl font-bold text-center">Create Account</Card.Title>
            <Card.Description class="text-center">
                Join Ruthful Hearts and start your journey
            </Card.Description>
        </Card.Header>
        <Card.Content>
            <form on:submit|preventDefault={handleSubmit} class="space-y-4">
                <div class="space-y-2">
                    <Label for="fullName">Full Name</Label>
                    <Input 
                        id="fullName"
                        type="text" 
                        placeholder="Enter your full name"
                        bind:value={fullName}
                        required
                    />
                </div>

                <div class="space-y-2">
                    <Label for="email">Email</Label>
                    <Input 
                        id="email"
                        type="email" 
                        placeholder="Enter your email"
                        bind:value={email}
                        required
                    />
                </div>
                
                <div class="space-y-2">
                    <Label for="password">Password</Label>
                    <Input 
                        id="password"
                        type="password" 
                        placeholder="Create a password"
                        bind:value={password}
                        required
                    />
                </div>

                <div class="space-y-2">
                    <Label for="confirmPassword">Confirm Password</Label>
                    <Input 
                        id="confirmPassword"
                        type="password" 
                        placeholder="Confirm your password"
                        bind:value={confirmPassword}
                        required
                    />
                </div>

                <div class="flex items-center space-x-2">
                    <Checkbox 
                        id="terms"
                        bind:checked={acceptTerms}
                        required
                    />
                    <label 
                        for="terms" 
                        class="text-sm text-gray-600"
                    >
                        I agree to the 
                        <a href="/terms" class="text-pink-600 hover:underline">Terms of Service</a>
                        and
                        <a href="/privacy" class="text-pink-600 hover:underline">Privacy Policy</a>
                    </label>
                </div>

                <Button type="submit" class="w-full bg-pink-600 hover:bg-pink-700">
                    Create Account
                </Button>

                <div class="text-center text-sm">
                    Already have an account?
                    <button 
                        type="button"
                        class="text-pink-600 hover:underline ml-1"
                        on:click={() => goto('/auth/login')}
                    >
                        Sign in
                    </button>
                </div>
            </form>
        </Card.Content>
    </Card.Root>
</div>
